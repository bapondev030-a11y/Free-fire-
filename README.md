```react
import React, { useState, useEffect } from 'react';
import { motion, AnimatePresence } from 'framer-motion';

// Font Awesome via CDN in the main HTML is assumed, 
// but we will use Lucide-React for performance and reliability 
// as it provides the same professional "FontAwesome" aesthetic.
import { 
  User, 
  Briefcase, 
  GraduationCap, 
  Mail, 
  Code, 
  ExternalLink, 
  Github, 
  Linkedin, 
  Terminal, 
  Cpu, 
  Layers,
  ChevronRight,
  Send,
  Download
} from 'lucide-react';

const COLORS = {
  bg: '#080616',
  surface: '#1A1953',
  primary: '#2F2FE4',
  secondary: '#162E93',
  text: '#FFFFFF',
  textMuted: '#94a3b8'
};

const App = () => {
  const [activeTab, setActiveTab] = useState('All');
  const [scrolled, setScrolled] = useState(false);

  useEffect(() => {
    const handleScroll = () => setScrolled(window.scrollY > 50);
    window.addEventListener('scroll', handleScroll);
    return () => window.removeEventListener('scroll', handleScroll);
  }, []);

  const fadeIn = {
    initial: { opacity: 0, y: 20 },
    whileInView: { opacity: 1, y: 0 },
    viewport: { once: true },
    transition: { duration: 0.6 }
  };

  const navItems = ['Home', 'About', 'Experience', 'Education', 'Portfolio', 'Contact'];

  return (
    <div className="min-h-screen text-white font-sans selection:bg-[#2F2FE4] selection:text-white" style={{ backgroundColor: COLORS.bg }}>
      
      {/* Navigation */}
      <nav className={`fixed top-0 w-full z-50 transition-all duration-500 ${scrolled ? 'py-4 backdrop-blur-lg border-b border-white/10 shadow-2xl' : 'py-8'}`}
           style={{ backgroundColor: scrolled ? `${COLORS.bg}cc` : 'transparent' }}>
        <div className="container mx-auto px-6 flex justify-between items-center">
          <motion.div 
            initial={{ opacity: 0, x: -20 }}
            animate={{ opacity: 1, x: 0 }}
            className="text-3xl font-black tracking-tighter"
          >
            <span style={{ color: COLORS.primary }}>NARUTO</span>
            <span className="text-white">.</span>
          </motion.div>
          
          <div className="hidden md:flex space-x-8">
            {navItems.map((item) => (
              <a key={item} href={`#${item.toLowerCase()}`} className="text-sm font-medium hover:text-[#2F2FE4] transition-colors uppercase tracking-widest">
                {item}
              </a>
            ))}
          </div>

          <motion.button 
            whileHover={{ scale: 1.05 }}
            whileTap={{ scale: 0.95 }}
            className="hidden md:block px-6 py-2 rounded-full font-bold text-sm border-2 border-[#2F2FE4] hover:bg-[#2F2FE4] transition-all"
          >
            HIRE ME
          </motion.button>
        </div>
      </nav>

      {/* Hero Section */}
      <section id="home" className="relative min-h-screen flex items-center pt-20 overflow-hidden">
        {/* Animated Background Orbs */}
        <div className="absolute top-[-10%] left-[-10%] w-[50%] h-[50%] rounded-full blur-[120px] opacity-20" style={{ backgroundColor: COLORS.primary }}></div>
        <div className="absolute bottom-[-10%] right-[-10%] w-[40%] h-[40%] rounded-full blur-[120px] opacity-20" style={{ backgroundColor: COLORS.secondary }}></div>

        <div className="container mx-auto px-6 grid md:grid-cols-2 gap-12 items-center relative z-10">
          <motion.div
            initial={{ opacity: 0, x: -50 }}
            animate={{ opacity: 1, x: 0 }}
            transition={{ duration: 0.8 }}
          >
            <h2 className="text-[#2F2FE4] font-mono font-bold tracking-widest mb-4">SYSTEMS ARCHITECT & DEVELOPER</h2>
            <h1 className="text-6xl md:text-8xl font-black mb-6 leading-none">
              Building Digital <br />
              <span className="text-transparent bg-clip-text bg-gradient-to-r from-[#2F2FE4] to-[#162E93]">Masterpieces.</span>
            </h1>
            <p className="text-lg text-slate-400 mb-8 max-w-lg leading-relaxed">
              Hello, I am Naruto. I specialize in crafting high-performance applications that merge technical excellence with stunning visual design.
            </p>
            <div className="flex flex-wrap gap-4">
              <button className="px-8 py-4 rounded-xl bg-[#2F2FE4] font-bold shadow-lg shadow-[#2F2FE4]/30 flex items-center gap-2 group hover:translate-y-[-2px] transition-all">
                Explore Projects <ChevronRight size={18} className="group-hover:translate-x-1 transition-transform" />
              </button>
              <button className="px-8 py-4 rounded-xl bg-white/5 border border-white/10 font-bold backdrop-blur-sm flex items-center gap-2 hover:bg-white/10 transition-all">
                <Download size={18} /> Download CV
              </button>
            </div>
          </motion.div>

          <motion.div 
            initial={{ opacity: 0, scale: 0.8, rotate: 5 }}
            animate={{ opacity: 1, scale: 1, rotate: 0 }}
            transition={{ duration: 1, type: "spring" }}
            className="relative"
          >
            <div className="absolute inset-0 bg-[#2F2FE4] blur-[60px] opacity-20 rounded-full scale-75"></div>
            <img 
              src="https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?auto=format&fit=crop&q=80&w=800" 
              alt="Naruto Profile" 
              className="relative z-10 rounded-[40px] border-2 border-white/10 shadow-2xl transform hover:scale-[1.02] transition-transform duration-500"
            />
            {/* Experience Badge */}
            <div className="absolute -bottom-6 -left-6 z-20 bg-[#1A1953] p-6 rounded-2xl border border-white/10 shadow-xl">
              <div className="text-4xl font-black text-[#2F2FE4]">08+</div>
              <div className="text-xs font-bold text-slate-400 tracking-tighter uppercase">Years of Experience</div>
            </div>
          </motion.div>
        </div>
      </section>

      {/* Stats Section */}
      <section className="py-12 border-y border-white/5 bg-white/[0.02]">
        <div className="container mx-auto px-6 grid grid-cols-2 md:grid-cols-4 gap-8">
          {[
            { label: 'Happy Clients', val: '150+' },
            { label: 'Projects Finished', val: '280+' },
            { label: 'Digital Assets', val: '1.2k' },
            { label: 'Lines of Code', val: '4M+' }
          ].map((stat, i) => (
            <motion.div key={i} {...fadeIn} className="text-center">
              <div className="text-3xl font-black mb-1">{stat.val}</div>
              <div className="text-xs text-slate-500 font-bold uppercase tracking-widest">{stat.label}</div>
            </motion.div>
          ))}
        </div>
      </section>

      {/* Experience & Skills */}
      <section id="experience" className="py-24 overflow-hidden">
        <div className="container mx-auto px-6">
          <div className="grid lg:grid-cols-2 gap-20">
            {/* Experience Column */}
            <motion.div {...fadeIn}>
              <h3 className="text-[#2F2FE4] font-bold mb-4 flex items-center gap-2 italic">
                <Briefcase size={20} /> Professional Journey
              </h3>
              <h2 className="text-4xl font-black mb-12">Experience</h2>
              
              <div className="space-y-8">
                {[
                  { title: "Lead Systems Architect", place: "TechFlow Systems", date: "2022 - Present", desc: "Overseeing cloud infrastructure and modernizing legacy codebases." },
                  { title: "Senior Full Stack Developer", place: "Digital Pulse", date: "2019 - 2022", desc: "Built scalable React/Node.js applications for international logistics firms." },
                  { title: "UI/UX Designer", place: "Creative Studio", date: "2017 - 2019", desc: "Designed intuitive interfaces used by over 500k monthly active users." }
                ].map((item, i) => (
                  <div key={i} className="group relative pl-8 border-l-2 border-white/5 hover:border-[#2F2FE4] transition-colors">
                    <div className="absolute top-0 left-[-9px] w-4 h-4 rounded-full bg-[#080616] border-2 border-white/20 group-hover:border-[#2F2FE4] group-hover:scale-125 transition-all"></div>
                    <div className="text-xs font-bold text-[#2F2FE4] mb-2">{item.date}</div>
                    <h4 className="text-xl font-bold mb-1">{item.title}</h4>
                    <div className="text-slate-400 mb-4">{item.place}</div>
                    <p className="text-sm text-slate-500 leading-relaxed">{item.desc}</p>
                  </div>
                ))}
              </div>
            </motion.div>

            {/* Skills Column */}
            <motion.div {...fadeIn} transition={{ delay: 0.2 }}>
              <h3 className="text-[#2F2FE4] font-bold mb-4 flex items-center gap-2 italic">
                <Cpu size={20} /> My Toolkit
              </h3>
              <h2 className="text-4xl font-black mb-12">Technical Skills</h2>
              
              <div className="grid grid-cols-2 gap-4">
                {[
                  { name: 'React / Next.js', level: '95%', icon: <Layers size={18} /> },
                  { name: 'Node.js / Express', level: '90%', icon: <Terminal size={18} /> },
                  { name: 'Python / Django', level: '85%', icon: <Code size={18} /> },
                  { name: 'UI / UX Design', level: '92%', icon: <User size={18} /> },
                  { name: 'Cloud Architecture', level: '88%', icon: <Cpu size={18} /> },
                  { name: 'PostgreSQL', level: '90%', icon: <Terminal size={18} /> }
                ].map((skill, i) => (
                  <div key={i} className="p-6 rounded-2xl bg-[#1A1953]/30 border border-white/5 hover:border-white/20 transition-all">
                    <div className="text-[#2F2FE4] mb-4">{skill.icon}</div>
                    <div className="flex justify-between items-end mb-2">
                      <span className="font-bold text-sm">{skill.name}</span>
                      <span className="text-[10px] font-bold text-slate-500">{skill.level}</span>
                    </div>
                    <div className="h-1 bg-white/10 rounded-full overflow-hidden">
                      <motion.div 
                        initial={{ width: 0 }}
                        whileInView={{ width: skill.level }}
                        transition={{ duration: 1.5, ease: "easeOut" }}
                        className="h-full bg-gradient-to-r from-[#162E93] to-[#2F2FE4]"
                      />
                    </div>
                  </div>
                ))}
              </div>
            </motion.div>
          </div>
        </div>
      </section>

      {/* Portfolio Section */}
      <section id="portfolio" className="py-24 bg-white/[0.01]">
        <div className="container mx-auto px-6">
          <div className="text-center mb-16">
            <motion.h2 {...fadeIn} className="text-5xl font-black mb-4 tracking-tighter">Selected Works</motion.h2>
            <motion.div {...fadeIn} className="flex justify-center gap-4 flex-wrap">
              {['All', 'Web App', 'Design', 'Mobile'].map(tab => (
                <button 
                  key={tab} 
                  onClick={() => setActiveTab(tab)}
                  className={`px-6 py-2 rounded-full text-xs font-bold tracking-widest transition-all ${activeTab === tab ? 'bg-[#2F2FE4] text-white' : 'bg-white/5 text-slate-400 hover:bg-white/10'}`}
                >
                  {tab.toUpperCase()}
                </button>
              ))}
            </motion.div>
          </div>

          <div className="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
            <AnimatePresence mode="popLayout">
              {[
                { title: 'Neural Finance', cat: 'Web App', img: 'https://images.unsplash.com/photo-1611974717525-58a457242ce1?auto=format&fit=crop&q=80&w=800' },
                { title: 'Skyline Real Estate', cat: 'Mobile', img: 'https://images.unsplash.com/photo-1460925895917-afdab827c52f?auto=format&fit=crop&q=80&w=800' },
                { title: 'Vortex UI Kit', cat: 'Design', img: 'https://images.unsplash.com/photo-1551288049-bebda4e38f71?auto=format&fit=crop&q=80&w=800' }
              ].filter(p => activeTab === 'All' || p.cat === activeTab).map((proj, i) => (
                <motion.div 
                  layout
                  initial={{ opacity: 0, scale: 0.9 }}
                  animate={{ opacity: 1, scale: 1 }}
                  exit={{ opacity: 0, scale: 0.9 }}
                  transition={{ duration: 0.4 }}
                  key={proj.title} 
                  className="group relative rounded-3xl overflow-hidden aspect-[4/5]"
                >
                  <img src={proj.img} alt={proj.title} className="w-full h-full object-cover grayscale group-hover:grayscale-0 group-hover:scale-110 transition-all duration-700" />
                  <div className="absolute inset-0 bg-gradient-to-t from-[#080616] via-transparent to-transparent opacity-90"></div>
                  <div className="absolute bottom-0 left-0 p-8 w-full translate-y-4 group-hover:translate-y-0 transition-transform">
                    <span className="text-[10px] font-bold text-[#2F2FE4] uppercase tracking-widest bg-[#2F2FE4]/10 px-3 py-1 rounded-full mb-3 inline-block border border-[#2F2FE4]/20">{proj.cat}</span>
                    <h3 className="text-2xl font-black mb-4">{proj.title}</h3>
                    <button className="flex items-center gap-2 text-sm font-bold opacity-0 group-hover:opacity-100 transition-opacity">
                      View Project <ExternalLink size={16} />
                    </button>
                  </div>
                </motion.div>
              ))}
            </AnimatePresence>
          </div>
        </div>
      </section>

      {/* Education */}
      <section id="education" className="py-24">
        <div className="container mx-auto px-6">
          <motion.div {...fadeIn} className="max-w-4xl mx-auto">
            <h2 className="text-4xl font-black mb-12 flex items-center gap-4">
               <GraduationCap size={40} className="text-[#2F2FE4]" /> Education
            </h2>
            <div className="space-y-6">
              {[
                { degree: "M.Sc. in Computer Science", school: "Global Institute of Technology", year: "2015 - 2017", grade: "GPA 3.9/4.0" },
                { degree: "B.Tech in Information Technology", school: "National Engineering College", year: "2011 - 2015", grade: "First Class Distinction" }
              ].map((edu, i) => (
                <div key={i} className="p-8 rounded-3xl bg-[#1A1953]/20 border border-white/5 hover:border-[#2F2FE4] transition-all flex flex-col md:flex-row justify-between md:items-center gap-4">
                  <div>
                    <h3 className="text-xl font-bold mb-1">{edu.degree}</h3>
                    <p className="text-slate-400 font-medium">{edu.school}</p>
                  </div>
                  <div className="text-right">
                    <div className="text-[#2F2FE4] font-bold mb-1">{edu.year}</div>
                    <div className="text-[10px] font-black uppercase text-slate-500 tracking-widest">{edu.grade}</div>
                  </div>
                </div>
              ))}
            </div>
          </motion.div>
        </div>
      </section>

      {/* Contact Section */}
      <section id="contact" className="py-24 relative overflow-hidden">
        <div className="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[100%] h-[100%] bg-[#2F2FE4] blur-[150px] opacity-10 rounded-full"></div>
        <div className="container mx-auto px-6 relative z-10">
          <div className="max-w-6xl mx-auto grid lg:grid-cols-2 gap-16 items-center">
            <motion.div {...fadeIn}>
              <h2 className="text-6xl font-black mb-8 leading-tight">Got a Project? <br /><span className="text-[#2F2FE4]">Let's Talk.</span></h2>
              <div className="space-y-6">
                <div className="flex items-center gap-6 group">
                  <div className="w-14 h-14 rounded-2xl bg-[#1A1953] flex items-center justify-center text-[#2F2FE4] group-hover:bg-[#2F2FE4] group-hover:text-white transition-all">
                    <Mail size={24} />
                  </div>
                  <div>
                    <div className="text-xs font-bold text-slate-500 uppercase tracking-widest">Email Me</div>
                    <div className="text-xl font-bold">contact@naruto.dev</div>
                  </div>
                </div>
                <div className="flex items-center gap-6 group">
                  <div className="w-14 h-14 rounded-2xl bg-[#1A1953] flex items-center justify-center text-[#2F2FE4] group-hover:bg-[#2F2FE4] group-hover:text-white transition-all">
                    <Linkedin size={24} />
                  </div>
                  <div>
                    <div className="text-xs font-bold text-slate-500 uppercase tracking-widest">LinkedIn</div>
                    <div className="text-xl font-bold">linkedin.com/in/naruto</div>
                  </div>
                </div>
              </div>
            </motion.div>

            <motion.div {...fadeIn} transition={{ delay: 0.2 }} className="bg-[#1A1953]/40 p-10 rounded-[40px] border border-white/5 backdrop-blur-xl">
              <form className="space-y-6" onSubmit={e => e.preventDefault()}>
                <div className="grid md:grid-cols-2 gap-6">
                  <div className="space-y-2">
                    <label className="text-[10px] font-bold uppercase tracking-widest text-slate-400 ml-2">Name</label>
                    <input type="text" className="w-full bg-[#080616]/50 border border-white/10 p-4 rounded-xl focus:border-[#2F2FE4] outline-none transition-all" placeholder="Naruto Uzumaki" />
                  </div>
                  <div className="space-y-2">
                    <label className="text-[10px] font-bold uppercase tracking-widest text-slate-400 ml-2">Email</label>
                    <input type="email" className="w-full bg-[#080616]/50 border border-white/10 p-4 rounded-xl focus:border-[#2F2FE4] outline-none transition-all" placeholder="naruto@dev.com" />
                  </div>
                </div>
                <div className="space-y-2">
                  <label className="text-[10px] font-bold uppercase tracking-widest text-slate-400 ml-2">Message</label>
                  <textarea rows="4" className="w-full bg-[#080616]/50 border border-white/10 p-4 rounded-xl focus:border-[#2F2FE4] outline-none transition-all resize-none" placeholder="Let's build something epic..."></textarea>
                </div>
                <button className="w-full py-5 bg-[#2F2FE4] rounded-xl font-black text-sm tracking-widest uppercase hover:bg-[#162E93] transition-all flex items-center justify-center gap-2 shadow-2xl shadow-[#2F2FE4]/40">
                  Submit Proposal <Send size={18} />
                </button>
              </form>
            </motion.div>
          </div>
        </div>
      </section>

      {/* Footer */}
      <footer className="py-12 border-t border-white/5 text-center">
        <div className="container mx-auto px-6">
          <div className="text-2xl font-black mb-6 tracking-tighter">
            <span style={{ color: COLORS.primary }}>NARUTO</span>.
          </div>
          <div className="flex justify-center gap-8 mb-8">
            <a href="#" className="p-3 bg-white/5 rounded-full hover:bg-[#2F2FE4] transition-all"><Github size={20} /></a>
            <a href="#" className="p-3 bg-white/5 rounded-full hover:bg-[#2F2FE4] transition-all"><Linkedin size={20} /></a>
            <a href="#" className="p-3 bg-white/5 rounded-full hover:bg-[#2F2FE4] transition-all"><ExternalLink size={20} /></a>
          </div>
          <p className="text-slate-500 text-sm font-medium tracking-tight">
            Designed & Engineered with ❤️ by Naruto
