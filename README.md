# Place-AR-model-SwiftUI-RealityKit
Place a blue cube AR model
# The first part
![IMG_1217](https://github.com/S-way520/Place-AR-model-SwiftUI-RealityKit/assets/95877651/b2738647-a6bc-4849-942c-b67fc0d650c9)
# The second part
Code file 1
```swift
import SwiftUI
@main
struct MyApp: App {
    var body: some Scene {
        WindowGroup {
            Reality()
        }
    }
}
```
Code file 2
```swift
import SwiftUI
import RealityKit
struct Reality: View {
    var body: some View {
        ARViewContainer().edgesIgnoringSafeArea(.all)
    }
}
struct ARViewContainer: UIViewRepresentable {
    func makeUIView(context: Context) -> ARView {
        
        // Create an ARView instance with AR camera mode and automatic session configuration
        let arView = ARView(frame: .zero, cameraMode: .ar, automaticallyConfigureSession: true)
        
        // Create an AnchorEntity representing a horizontal plane
        let anchorEntity = AnchorEntity(plane: .horizontal)//水平类锚点
        
        // Generate a box mesh resource with a specific size and corner radius
        let box = MeshResource.generateBox(size: 0.2/2, cornerRadius: 0.05/5)//形状
        
        // Create a SimpleMaterial with blue color and metallic properties
        let material = SimpleMaterial(color: .blue, isMetallic: true)//颜色
        
        // Create a ModelEntity with the box mesh and the material
        let ARentity = ModelEntity(mesh: box, materials: [material])//实体(加载模型)
        
        // Add the ModelEntity as a child of the AnchorEntity
        anchorEntity.addChild(ARentity)
        
        // Add the AnchorEntity to the ARView's scene anchors
        arView.scene.anchors.append(anchorEntity)//场景
        
        // Return the ARView
        return arView
    }
    func updateUIView(_ uiView: ARView, context: Context) {
        // The updateUIView function is empty for now
        // You can add code here to handle updates to the view if needed
    }
}
```
