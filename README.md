<!DOCTYPE html>
<html lang="en" class="dark">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sai Surya Nelakurthi - AI & Full-Stack Developer</title>
        <script src="https://cdn.tailwindcss.com"></script>
        <script src="https://unpkg.com/react@18/umd/react.development.js"></script>
    <script src="https://unpkg.com/react-dom@18/umd/react-dom.development.js"></script>
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
    
        <style type="text/tailwindcss">
        @layer base {
            html {
                font-family: 'Inter', sans-serif;
            }
        }
    </style>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;700&display=swap" rel="stylesheet">
    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    colors: {
                        'brand': {
                            'light': '#3b82f6', // blue-500
                            'dark': '#60a5fa'  // blue-400
                        },
                        'bkg': '#0a0a0a',
                        'card': '#1a1a1a',
                        'text-primary': '#f5f5f5',
                        'text-secondary': '#a3a3a3',
                    },
                    animation: {
                        'fade-in': 'fadeIn 0.5s ease-out',
                    },
                    keyframes: {
                         fadeIn: {
                            '0%': { opacity: 0, transform: 'translateY(10px)' },
                            '100%': { opacity: 1, transform: 'translateY(0)' },
                        },
                    },
                },
            },
        }
    </script>
</head>
<body class="bg-bkg text-text-primary antialiased">
    <div id="root"></div>

        <script type="text/babel">

        const { useState, useEffect } = React;
        
        // --- Inline SVG Icons (to fix lucide errors) ---
        const SvgIcon = ({ size = 24, className = "", children }) => (
            <svg
                xmlns="http://www.w3.org/2000/svg"
                width={size}
                height={size}
                viewBox="0 0 24 24"
                fill="none"
                stroke="currentColor"
                strokeWidth="2"
                strokeLinecap="round"
                strokeLinejoin="round"
                className={className}
            >
                {children}
            </svg>
        );

        const Mail = ({ size, className }) => (
            <SvgIcon size={size} className={className}>
                <rect width="20" height="16" x="2" y="4" rx="2" />
                <path d="m22 7-8.97 5.7a1.94 1.94 0 0 1-2.06 0L2 7" />
            </SvgIcon>
        );

        const Linkedin = ({ size, className }) => (
            <SvgIcon size={size} className={className}>
                <path d="M16 8a6 6 0 0 1 6 6v7h-4v-7a2 2 0 0 0-2-2 2 2 0 0 0-2 2v7h-4v-7a6 6 0 0 1 6-6z" />
                <rect width="4" height="12" x="2" y="9" />
                <circle cx="4" cy="4" r="2" />
            </SvgIcon>
        );

        const Github = ({ size, className }) => (
            <SvgIcon size={size} className={className}>
                <path d="M15 22v-4a4.8 4.8 0 0 0-1-3.5c3 0 6-1.5 6-6.5a5.4 5.4 0 0 0-1.5-3.75a5 5 0 0 0-.1-3.75s-1.1-.3-3.5 1.3a12.3 12.3 0 0 0-6.2 0C6.5 2.8 5.4 3.1 5.4 3.1a5 5 0 0 0-.1 3.75A5.4 5.4 0 0 0 4 10.5c0 5 3 6.5 6 6.5a4.8 4.8 0 0 0-1 3.5v4" />
            </SvgIcon>
        );
        
        const Database = ({ size, className }) => (
            <SvgIcon size={size} className={className}>
                <ellipse cx="12" cy="5" rx="9" ry="3" />
                <path d="M3 5V19A9 3 0 0 0 21 19V5" />
                <path d="M3 12A9 3 0 0 0 21 12" />
            </SvgIcon>
        );

        const Code = ({ size, className }) => (
            <SvgIcon size={size} className={className}>
                <polyline points="16 18 22 12 16 6" />
                <polyline points="8 6 2 12 8 18" />
            </SvgIcon>
        );

        const Layers = ({ size, className }) => (
            <SvgIcon size={size} className={className}>
                <polygon points="12 2 2 7 12 12 22 7 12 2" />
                <polyline points="2 17 12 22 22 17" />
                <polyline points="2 12 12 17 22 12" />
            </SvgIcon>
        );

        const Server = ({ size, className }) => (
            <SvgIcon size={size} className={className}>
                <rect width="20" height="8" x="2" y="2" rx="2" ry="2" />
                <rect width="20" height="8" x="2" y="14" rx="2" ry="2" />
                <line x1="6" x2="6.01" y1="6" y2="6" />
                <line x1="6" x2="6.01" y1="18" y2="18" />
            </SvgIcon>
        );

        const Cloud = ({ size, className }) => (
            <SvgIcon size={size} className={className}>
                <path d="M17.5 19H9a7 7 0 1 1 6.71-9h1.79a4.5 4.5 0 1 1 0 9Z" />
            </SvgIcon>
        );

        const Brain = ({ size, className }) => (
            <SvgIcon size={size} className={className}>
                <path d="M12 5a3 3 0 1 0-5.993.142" />
                <path d="M12 5a3 3 0 1 1 5.993.142" />
                <path d="M15 13a3 3 0 1 0-5.993.142" />
                <path d="M15 13a3 3 0 1 1 5.993.142" />
                <path d="M9 13a3 3 0 1 0-5.993.142" />
                <path d="M9 13a3 3 0 1 1 5.993.142" />
                <path d="m13.5 7.6-1-1.6" />
                <path d="m10.5 7.6 1-1.6" />
                <path d="m12 10.5 1.5 2.5" />
                <path d="m12 10.5-1.5 2.5" />
                <path d="m10.5 15.4 1 1.6" />
                <path d="m13.5 15.4-1 1.6" />
                <path d="M17.5 10a2.5 2.5 0 1 0-4.994.129" />
                <path d="M17.5 10a2.5 2.5 0 1 1 4.994.129" />
                <path d="M6.5 10a2.5 2.5 0 1 0-4.994.129" />
                <path d="M6.5 10a2.5 2.5 0 1 1 4.994.129" />
                <path d="M12 13a3 3 0 1 1-5.993.142" />
                <path d="M12 13a3 3 0 1 0 5.993.142" />
            </SvgIcon>
        );
        
        const Briefcase = ({ size, className }) => (
            <SvgIcon size={size} className={className}>
                <rect width="20" height="14" x="2" y="7" rx="2" ry="2" />
                  <path d="M16 21V5a2 2 0 0 0-2-2h-4a2 2 0 0 0-2 2v16" />
            </SvgIcon>
        );
        // -------------------------------------------------------------------

        // --- YOUR Portfolio Data ---
        const portfolioData = {
            name: "Sai Surya Nelakurthi",
            headline: "AI & Full-Stack Developer",
            email: "nelakurthisaisurya@gmail.com",
            linkedin: "https://www.linkedin.com/in/saisuryanelakurthi/",
            github: "https://github.com/saisuryanelakurthi",
            about: "I am a Full-Stack Developer specializing in building and integrating AI-powered applications, currently completing my M.Sc. in Applied Computer Science at SRH University. My expertise lies in building scalable, production-ready systems that leverage the power of modern AI using TypeScript, React, Node.js, and Python.",
            projects: [
                {
                    title: "Full-Stack AI Application",
                    company: "Radarprotest (Working Student)",
                    description: "Building a full-stack AI application from scratch. It uses OpenAI's GPT-4o Vision to analyze documents and Ideogram for AI image generation.",
                    tech: ["React", "TypeScript", "Node.js", "OpenAI API", "Drizzle ORM", "PostgreSQL", "Google Cloud Storage", "Tailwind CSS"],
                    icon: Brain
                },
                // --- ADDED INTERNSHIP ---
                {
                    title: "Python Full Stack Internship",
                    company: "ADHOC Network",
                    description: "Developed and deployed web applications using Python (Django, Flask), React, and Angular. Designed responsive front-end interfaces and implemented RESTful APIs.",
                    tech: ["Python", "Django", "Flask", "React", "Angular.js", "REST APIs", "Git"],
                    icon: Briefcase
                  },
                  // --- END ADDED INTERNSHIP ---
                  {
                    title: "Fitness Dashboard App",
                    company: "University Project",
                    description: "A real-time data pipeline that simulates smartwatch data (heart rate, pace) and visualizes it in a live dashboard.",
                    tech: ["Python", "Flask", "InfluxDB", "Grafana", "MongoDB", "Qdrant", "REST APIs"],
                    icon: Database
                },
                  {
                      title: "AI-Powered Code Review",
                      company: "University Seminar",
                      description: "Research presentation on 'AICodeReview,' an IntelliJ plugin using GPT-3.5 to find bugs, logic errors, and security issues in code.",
                      tech: ["AI Integration", "GPT-3.5", "Code Analysis", "IntelliJ IDEA"],
                       icon: Code
                  },
                  {
                      title: "Cloud Deployment Analysis",
                       company: "University Project",
                       description: "A comparative analysis of Google Kubernetes Engine (GKE) and Google App Engine (GAE) for deploying scalable cloud applications.",
                          tech: ["GKE", "GAE", "Docker", "Kubernetes", "Cloud SQL", "Load Testing"],
                      icon: Cloud
                  },
                  {
                          title: "Library Management System",
                       company: "University Project",
                       description: "Developed a full-stack Library Management System using Spring Boot (Java) for the backend and HTML/Bootstrap/CSS for the frontend with a MySQL database.",
                      tech: ["Java", "Spring Boot", "MySQL", "REST APIs", "HTML", "Bootstrap"],
                      icon: Code
                  },
                  {
                          title: "SRH Hospital Companion",
                      company: "University Project",
                      description: "Applied formal project management methodologies to plan a pre-planned surgery companion app. Focused on balancing scope, time, and cost.",
                      tech: ["Agile", "Scrum", "V-Model", "Waterfall Model", "Project Management"],
                      icon: Briefcase
                  },
            ],
            // --- SKILLS SECTION UPDATED ---
            skills: [
                {
                    category: "AI & ML",
                    items: ["Generative Al", "OpenAI API", "Al Integration", "Code Analysis"],
                    icon: Brain
                },
                  {
                          category: "Cloud/DevOps",
                          items: ["Kubernetes (GKE)", "Docker", "Google App Engine (GAE)", "Google Cloud Storage", "Git"],
                          icon: Cloud
                   },
                     {
                           category: "Databases",
                           items: ["PostgreSQL", "Drizzle ORM", "MongoDB", "MySQL"],
                            icon: Database
                     },
                     {
                           category: "Frontend",
                           items: ["React", "HTML5", "CSS"],
                            icon: Layers
                     },
                     {
                           category: "Backend",
                           // --- ITEMS REMOVED HERE ---
                           items: ["TypeScript", "Python", "Flask", "REST APIs"],
                            icon: Server
                     },
                     {
                           category: "Enterprise",
                           items: ["Agile", "Scrum"],
                            icon: Briefcase
                     }
                 ]
                  // --- END OF UPDATED SKILLS ---
        };

        // --- Reusable Components ---
        const IconLink = ({ href, icon: Icon, label }) => (
            <a
                href={href}
                target="_blank"
                rel="noopener noreferrer"
                title={label}
                className="text-text-secondary hover:text-brand-dark transition-colors"
            >
                <Icon size={24} />
            </a>
        );
        
          const NavLink = ({ label, active, onClick }) => (
              <button
                  onClick={onClick}
                  className={`relative px-3 py-2 text-sm font-medium transition-colors
                      ${active
                              ? 'text-text-primary'
                              : 'text-text-secondary hover:text-text-primary'
                      }
                  `}
              >
                  {label}
                  {active && (
                          <span className="absolute bottom-0 left-1/2 -translate-x-1/2 w-1/2 h-0.5 bg-brand-dark rounded-full"></span>
                  )}
              </button>
        );

        const Tag = ({ children }) => (
            <span className="inline-block bg-brand-dark/10 text-brand-dark text-xs font-medium px-2 py-1 rounded-full whitespace-nowrap">
                  {children}
            </span>
        );

          // --- Page Components ---

          const Header = ({ activePage, setActivePage }) => {
              const navItems = ['Home', 'Projects', 'Skills', 'Contact'];

              return (
                  <header className="sticky top-0 left-0 right-0 z-10 bg-bkg/80 backdrop-blur-sm border-b border-card">
                          <nav className="max-w-4xl mx-auto p-4 flex justify-between items-center">
                              <span className="text-lg font-bold text-text-primary">{portfolioData.name}</span>
                              <div className="hidden sm:flex items-center space-x-2">
                                  {navItems.map(item => (
                                      <NavLink
                                          key={item}
                                          label={item}
                                          active={activePage === item.toLowerCase()}
                                          onClick={() => setActivePage(item.toLowerCase())}
                                      />
                                  ))}
                              </div>
                              <div className="flex sm:hidden items-center space-x-4">
                                  <IconLink href={portfolioData.linkedin} icon={Linkedin} label="LinkedIn" />
                                  <IconLink href={portfolioData.github} icon={Github} label="GitHub" />
                                  <IconLink href={`mailto:${portfolioData.email}`} icon={Mail} label="Email" />
                              </div>
                          </nav>
                          {/* Mobile Nav */}
                          <div className="sm:hidden flex justify-center items-center space-x-4 pb-3 border-b border-card/50">
                              {navItems.map(item => (
                                  <NavLink
                                      key={item}
                                      label={item}
                                      active={activePage === item.toLowerCase()}
                                      onClick={() => setActivePage(item.toLowerCase())}
                                  />
                              ))}
                          </div>
                  </header>
              );
          };

          const HomePage = () => (
              <section className="animate-fade-in max-w-4xl mx-auto py-16 sm:py-24 px-4">
                  <div className="flex flex-col md:flex-row items-center justify-center gap-12">
                          
                          {/* --- IMAGE COLUMN REMOVED --- */}

                          {/* --- UPDATED TEXT CONTAINER --- */}
                          <div className="text-center md:text-left">
                              <h1 className="text-4xl sm:text-5xl font-bold text-text-primary">
                                  {portfolioData.headline}
                              </h1>
                              <p className="mt-6 text-lg text-text-secondary">
                                  {portfolioData.about}
                              </p>
                              <div className="mt-10 flex justify-center md:justify-start items-center space-x-6">
                                  <a
                                      href={`mailto:${portfolioData.email}`}
                                      className="bg-brand-light text-white font-medium px-6 py-3 rounded-lg shadow-lg hover:bg-brand-dark transition-all w-full sm:w-auto flex items-center justify-center space-x-2"
                                  >
                                      <Mail size={20} />
                                      <span>Get In Touch</span>
                                  </a>
                                  <a
                                      href={portfolioData.github}
                                      target="_blank"
                                      rel="noopener noreferrer"
                                      className="text-text-secondary hover:text-brand-dark transition-colors flex items-center space-x-2"
                                  >
                                      <Github size={24} />
                                      <span>GitHub</span>
                                  </a>
                                  <a
                                      href={portfolioData.linkedin}
                                      target="_blank"
                                      rel="noopener noreferrer"
                                      className="text-text-secondary hover:text-brand-dark transition-colors flex items-center space-x-2"
                                  >
                                      <Linkedin size={24} />
                                      <span>LinkedIn</span>
                                  </a>
                              </div>
                          </div>
                          {/* --- END UPDATED TEXT CONTAINER --- */}
                  </div>
              </section>
        );

          const ProjectsPage = () => (
              <section className="animate-fade-in max-w-4xl mx-auto py-16 px-4">
                  <h2 className="text-3xl font-bold text-text-primary mb-8">Projects & Experience</h2>
                  <div className="grid grid-cols-1 md:grid-cols-2 gap-6">
                          {portfolioData.projects.map(project => (
                              <div key={project.title} className="bg-card border border-white/10 rounded-xl p-6 transition-all hover:border-brand-dark/50 hover:shadow-xl">
                                  <div className="flex items-center space-x-3 mb-4">
                                      <project.icon size={24} className="text-brand-dark" />
                                      <h3 className="text-xl font-semibold text-text-primary">{project.title}</h3>
                                  </div>
                                  <span className="text-sm font-medium text-text-secondary">{project.company}</span>
                                  <p className="mt-3 text-text-secondary text-sm mb-4">{project.description}</p>
                                  <div className="flex flex-wrap gap-2">
                                      {/* --- THIS IS THE FIX --- */}
                                      {project.tech.map(tech => <Tag key={tech}>{tech}</Tag>)}
                                  </div>
                              </div>
                          ))}
                  </div>
              </section>
        );

          const SkillsPage = () => (
              <section className="animate-fade-in max-w-4xl mx-auto py-16 px-4">
                  <h2 className="text-3xl font-bold text-text-primary mb-8">Core Skills</h2>
                  <div className="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-6">
                          {portfolioData.skills.map(skillCategory => (
                              <div key={skillCategory.category} className="bg-card border border-white/10 rounded-xl p-6">
                                  <div className="flex items-center space-x-3 mb-4">
                                      <skillCategory.icon size={24} className="text-brand-dark" />
                                      <h3 className="text-lg font-semibold text-text-primary">{skillCategory.category}</h3>
                                  </div>
                                  <ul className="space-y-2">
                                      {skillCategory.items.map(item => (
                                          <li key={item} className="text-text-secondary text-sm">{item}</li>
                                      ))}
                                  </ul>
                              </div>
                          ))}
                  </div>
              </section>
        );

          const ContactPage = () => (
              <section className="animate-fade-in max-w-xl mx-auto py-16 sm:py-24 px-4 text-center">
                  <h2 className="text-3xl font-bold text-text-primary mb-4">Let's Connect</h2>
                  <p className="text-lg text-text-secondary mb-8">
                          I'm actively seeking a full-time AI or Full-Stack position in Germany. 
                          I'd love to discuss how I can bring value to your team.
                   </p>
                  <div className="flex flex-col sm:flex-row justify-center items-center gap-6">
                          <a
                              href={`mailto:${portfolioData.email}`}
                              className="bg-brand-light text-white font-medium px-6 py-3 rounded-lg shadow-lg hover:bg-brand-dark transition-all w-full sm:w-auto flex items-center justify-center space-x-2"
                          >
                              <Mail size={20} />
                              <span>Email Me</span>
                          </a>
                          <a
                              href={portfolioData.linkedin}
                              target="_blank"
                              rel="noopener noreferrer"
                              className="bg-card border border-white/10 text-text-primary font-medium px-6 py-3 rounded-lg hover:border-brand-dark/50 transition-all w-full sm:w-auto flex items-center justify-center space-x-2"
                          >
                              <Linkedin size={20} />
                              <span>LinkedIn</span>
                          </a>
                          <a
                              href={portfolioData.github}
                              target="_blank"
                              rel="noopener noreferrer"
                              className="bg-card border border-white/10 text-text-primary font-medium px-6 py-3 rounded-lg hover:border-brand-dark/50 transition-all w-full sm:w-auto flex items-center justify-center space-x-2"
                          >
                              <Github size={20} />
                              <span>GitHub</span>
                          </a>
                  </div>
              </section>
        );
        
        const Footer = () => (
            <footer className="max-w-4xl mx-auto p-8 text-center border-t border-card">
                 <p className="text-sm text-text-secondary">
                    Designed & Built by Sai Surya Nelakurthi.
                </p>
            </footer>
        );

        // --- Main App Component ---
         const App = () => {
            const [activePage, setActivePage] = useState('home');

            const renderPage = () => {
                switch (activePage) {
                    case 'projects':
                        return <ProjectsPage />;
                    case 'skills':
                        return <SkillsPage />;
                    case 'contact':
                        return <ContactPage />;
                    case 'home':
                    default:
                        return <HomePage />;
                }
            };

            return (
                <div className="min-h-screen flex flex-col">
                     <Header activePage={activePage} setActivePage={setActivePage} />
                     <main className="flex-grow">
                         {renderPage()}
                     </main>
                     <Footer />
                </div>
            );
        };

          // --- Mount the App ---
         const root = ReactDOM.createRoot(document.getElementById('root'));
          root.render(<App />);

    </script>
</body>
</html>
