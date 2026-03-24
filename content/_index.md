---
# Leave the homepage title empty to use the site title
title: ''
summary: ''
date: 2026-01-05
type: landing

design:
  # Default section spacing
  spacing: '0'

sections:
  # Developer Hero - Gradient background with name, role, social, and CTAs
  - block: dev-hero
    id: hero
    content:
      username: me
      greeting: "Hi, I'm"
      show_status: true
      show_scroll_indicator: true
      typewriter:
        enable: true
        prefix: "I build"
        strings:
          - "AI-powered RAG systems"
          - "autonomous robots"
          - "scalable FastAPI backends"
          - "intelligent ETL pipelines"
        type_speed: 70
        delete_speed: 40
        pause_time: 2500
      cta_buttons:
        - text: View My Work
          url: "#projects"
          icon: arrow-down
        - text: Get In Touch
          url: "#contact"
          icon: envelope
    design:
      style: centered
      avatar_shape: circle
      animations: true
      background:
        color:
          light: "#fafafa"
          dark: "#0a0a0f"
      spacing:
        padding: ["6rem", "0", "4rem", "0"]
  
  # Filterable Portfolio - Alpine.js powered project filtering
  - block: portfolio
    id: projects
    content:
      title: "Featured Projects"
      subtitle: "A selection of my recent work"
      count: 0
      filters:
        folders:
          - projects
      buttons:
        - name: All
          tag: '*'
        - name: Full-Stack
          tag: Full-Stack
        - name: Frontend
          tag: Frontend
        - name: Backend
          tag: Backend
      default_button_index: 0
      # Archive link auto-shown if more projects exist than 'count' above
      # archive:
      #   enable: false  # Set to false to explicitly hide
      #   text: "Browse All"  # Customize text
      #   link: "/work/"  # Custom URL
    design:
      columns: 3
      background:
        color:
          light: "#ffffff"
          dark: "#0d0d12"
      spacing:
        padding: ["4rem", "0", "4rem", "0"]
  
  # Visual Tech Stack - Icons organized by category
  - block: tech-stack
    id: skills
    content:
      title: "Tech Stack"
      subtitle: "Technologies I use to build things"
      categories:
        - name: Languages
          items:
            - name: Python
              icon: devicon/python
            - name: C / C++
              icon: devicon/cplusplus
            - name: HTML
              icon: devicon/html5
            - name: JavaScript
              icon: devicon/javascript
        - name: AI & ML
          items:
            - name: RAG / LLMs
              icon: devicon/pytorch
            - name: Chroma DB
              icon: devicon/python
            - name: PyTorch
              icon: devicon/pytorch
            - name: Docker
              icon: devicon/docker
        - name: Backend
          items:
            - name: FastAPI
              icon: devicon/fastapi
            - name: Flask
              icon: devicon/flask
            - name: Firebase
              icon: devicon/firebase
            - name: PostgreSQL
              icon: devicon/postgresql
        - name: Robotics
          items:
            - name: ROS2 / Nav2
              icon: devicon/linux
            - name: micro-ROS
              icon: devicon/embeddedc
            - name: MATLAB
              icon: devicon/matlab
            - name: Git / GitHub
              icon: brands/github
    design:
      style: grid
      show_levels: false
      background:
        color:
          light: "#f5f5f5"
          dark: "#08080c"
      spacing:
        padding: ["4rem", "0", "4rem", "0"]
  
  # Experience Timeline
  - block: resume-experience
    id: experience
    content:
      title: Experience
      date_format: Jan 2006
      items:
        - title: Intern — Robotics & Automation
          company: Galexon Engineering Industries
          company_url: ''
          company_logo: ''
          location: Kerala, India
          date_start: '2025-06-01'
          date_end: '2025-06-27'
          description: |2-
            * Assisted in development and maintenance of automated control systems
            * Conducted diagnostic tests on robotic subsystems to resolve integration bottlenecks
            * Programmed and debugged PLC logic for sequential manufacturing automation
            * Created digital twins for offline robotic simulation using RoboDK
    design:
      columns: '1'
      background:
        color:
          light: "#ffffff"
          dark: "#0d0d12"
      spacing:
        padding: ["4rem", "0", "4rem", "0"]
  
  # Recent Blog Posts
  - block: collection
    id: blog
    content:
      title: Recent Posts
      subtitle: 'Notes on AI, robotics, and software engineering'
      text: ''
      filters:
        folders:
          - blog
        exclude_featured: false
      count: 3
      order: desc
    design:
      view: card
      columns: 3
      background:
        color:
          light: "#f5f5f5"
          dark: "#08080c"
      spacing:
        padding: ["4rem", "0", "4rem", "0"]
  
  # Contact Section
  - block: contact-info
    id: contact
    content:
      title: Get In Touch
      subtitle: "Let's build something amazing together"
      text: |-
        I'm a final-year Robotics & Automation student specializing in AI systems and backend engineering.
        Whether you're looking to hire, collaborate, or just want to say hi, feel free to reach out!
      email: joshincherian5@gmail.com
      autolink: true
    design:
      columns: '1'
      background:
        color:
          light: "#ffffff"
          dark: "#0d0d12"
      spacing:
        padding: ["4rem", "0", "4rem", "0"]
  
  # CTA Card
  - block: cta-card
    content:
      title: "Open to Opportunities"
      text: |-
        I'm a final-year B.Tech student actively looking for **Software Engineering**, **AI/ML**, or **Robotics** roles.
        
        Let's connect and build something great together.
      button:
        text: 'Download Resume'
        url: uploads/joshin_resume.pdf
        new_tab: true
    design:
      card:
        # Light mode: soft pastel theme gradient | Dark mode: rich deep gradient
        css_class: 'bg-gradient-to-br from-primary-200 via-primary-100 to-secondary-200 dark:from-primary-600 dark:via-primary-700 dark:to-secondary-700'
        text_color: dark
      background:
        color:
          light: "#f5f5f5"
          dark: "#08080c"
      spacing:
        padding: ["4rem", "0", "6rem", "0"]
---
