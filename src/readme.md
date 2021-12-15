# Create app
npx create-react-app my-app
cd my-app

# Install dependencies
npm install three @react-three/fiber

# Start
npm run start

# index.css
html,
body {
  margin: 0;
  overflow: hidden;
}

.App {
  width: 100vw;
  height: 100vh;
}

# App.js
import React, { useState }  from "react";
import { Canvas, useFrame } from "@react-three/fiber";

function MyRotatingBox() {
  const myMesh = React.useRef();
  const [active, setActive] = useState(false);

  useFrame(({ clock }) => {
    const a = clock.getElapsedTime();
    myMesh.current.rotation.x = a;
  });

  return (
    <mesh
      scale={active ? 1.5 : 1}
      onClick={() => setActive(!active)}
      ref={myMesh}
    >
      <boxBufferGeometry />
      <meshPhongMaterial color="royalblue" />
    </mesh>
  );
}

function App() {
  return (
    <div className="App">
      <Canvas>
        <MyRotatingBox />
        <ambientLight intensity={0.1} />
        <directionalLight />
      </Canvas>
    </div>
  );
}

export default App;

# remove React Files
logo.svg
reportWebVitals.js
setupTests.js

# Don't generate map files
"build": "GENERATE_SOURCEMAP=false react-scripts build",