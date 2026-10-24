I want to establish frontend design of an electron app. Read what the app is in OpenSensei.md 
Your goal is to prepare this repository for Claude to generate 4 distinct UI mockups based on design themes mentioned below. DO NOT build the UI yet.
Make sure the context window remains moderate and Claude is empowered to create the most creative UI designs possible, following these constraints. Do not make the output MD files chunky.

Your inputs:
1. I have 2 image references & a .excalidraw inside design/inputs. 
2. the .excalidraw is the source of truth for layout (the PNG is a visual check).the 1st reference image is the design layout i've made in excalidraw. all UI elements must be placed exactly like that.
3. ref-claude-desktop.png is from Claude desktop UI. I love the ultra minimalism, color themes and warm feeling and want to take Claude inspiration from that UI.
4. Anthropic's frontend-design skill

Your outputs:
1. Write design/LAYOUT-main.md: every region, its position/size relative to the window,
   a CSS grid-template proposal, what scrolls, and any ambiguity you found. Do not
   improve or reinterpret the layout. The excalidraw layout is already ultra-minimal so the agent must follow that.
2. In .cursor/rules/design.mdc write 10-12 bullets on what makes a website feel warm, welcoming, elegant, cozy, wholesome and minimal, & what design choices signal user's brain to mentally transition into a **calm, clear, focused, Zen-like study state**.
3. Fill in Agents.MD to briefly tell the agent what OpenSensei app is about, what agent is supposed to achieve, and few rules. Do not remove existing rules unless contradictory.

Design theme:
1. The experience should be **very minimal, professional, elegant, warm, cozy, wholesome, and welcoming**. Opening OpenSensei should help a student mentally transition into a **calm, clear, focused, Zen-like study state**. 
2. Keep only the absolutely necessary visual elements and remove others. Only dark mode.
3. Colors must be warm: orange-ish, brownish, near-black background, perhaps slate black, inspired by Claude web app's UI. Anthropic uses a terracotta or warm-clay accent (often near #D97757 — Anthropic's own Claude-interaction accent, so on a user's brief it reads as a tell); More instructions in frontend-design skill.
4. Emphasize that roadmap's presentation is foundational to this app. It's visual appeal is a core judging factor. More instructions in OpenSensei.md

Stop and show me all the files. Do not build any UI yet.