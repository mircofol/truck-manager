import React, { useState, useEffect, useRef } from 'react';
import {
  Truck, FileText, Wrench, RefreshCw,
  Download, CheckCircle2,
  CalendarDays, Play, Square,
  LogOut, Route,
  Clock, AlertTriangle,
  Thermometer, Calendar,
  Waves, Power, Upload, Trash2, File,
  History, Fuel, Euro
} from 'lucide-react';

const App = () => {
  const GOOGLE_SCRIPT_URL = ""; // Inserire URL Google Apps Script

  // Colori Tema
  const COLORS = {
    primary: '#791E53', // Viola Simbolo
    bg: '#111011',      // Sfondo Nero
    surface: '#1c1b1c', // Superficie card
    text: '#e2e2e2',
    muted: '#888888',
    danger: '#dc2626'
  };

  // Stati di Accesso
  const [isLogged, setIsLogged] = useState(() => {
    try {
      return localStorage.getItem('sm_logged') === 'true';
    } catch {
      return false;
    }
  });
 
  const [autista, setAutista] = useState(() => {
    try {
      return localStorage.getItem('sm_autista') || '';
    } catch {
      return '';
    }
  });

  const [targa, setTarga] = useState(() => {
    try {
      return localStorage.getItem('sm_targa') || '';
    } catch {
      return '';
    }
  });
 
  // Stati Generali App
  const [tab, setTab] = useState('operativo');
  const [inInvio, setInInvio] = useState(false);
  const [location, setLocation] = useState(null);
  const [notifica, setNotifica] = useState({ mostra: false, messaggio: '', tipo: '' });
 
  // STATO CARICO
  const [nDistinta, setNDistinta] = useState('');
  const [statoCarico, setStatoCarico] = useState('fermo');
  const [secondi, setSecondi] = useState(0);
  const [cronologiaDistinte, setCronologiaDistinte] = useState(() => {
    try {
      const saved = localStorage.getItem('sm_cronologia_distinte');
      return saved ? JSON.parse(saved) : [];
    } catch {
      return [];
    }
  });
  const timerRef = useRef(null);
 
  // STATO KM
  const [kmInizio, setKmInizio] = useState('');
  const [kmFine, setKmFine] = useState('');
  const [viaggioInCorso, setViaggioInCorso] = useState(false);

  // STATO CELLA FRIGO
  const [frigoAttivo, setFrigoAttivo] = useState(false);
  const [secondiFrigo, setSecondiFrigo] = useState(0);
  const frigoTimerRef = useRef(null);

  // STATI ALTRI TAB
  const [guasto, setGuasto] = useState({ componente: '', descrizione: '', urgenza: 'bassa' });
  const [assenza, setAssenza] = useState({ tipo: 'ferie', dal: '', al: '' });

  // STATO CARBURANTE
  const [carburante, setCarburante] = useState({ litri: '', euro: '' });
  const [storicoCarburante, setStoricoCarburante] = useState(() => {
    try {
      const saved = localStorage.getItem('sm_storico_carburante');
      return saved ? JSON.parse(saved) : [];
    } catch {
      return [];
    }
  });

  // STATO DOCUMENTI PERSONALI
  const [documentiCaricati, setDocumentiCaricati] = useState([]);
  const fileInputRef = useRef(null);

  const elencoAutisti = ["Aracu F.", "Baldussu P.", "Carta S.", "Corona A.", "Demurtas R.", "Deplano D.", "Dessi F.", "Ferrigno M.", "Fois G.", "Lamanna N.", "Lecis F.", "Crastus A.", "Licheri G.", "Lorrai F.", "Mannu W.", "Melis R.", "Meloni N.", "Mereu R.", "Mulana D.", "Murru G.", "Pinna G.", "Pinna I.", "Porcu A.", "Rachel S.", "Sarritzu A.", "Scalas R.", "Serra P.", "Setzu E.", "Toro A.", "Toro S.", "Zara J.", "Vargiu M.", "Sollai R.", "Impera A.", "Ledda E.", "Pili S.", "Soddu M."].sort();

  // Timer Carico
  useEffect(() => {
    if (statoCarico === 'in_corso') {
      timerRef.current = setInterval(() => setSecondi(prev => prev + 1), 1000);
    } else {
      clearInterval(timerRef.current);
    }
    return () => clearInterval(timerRef.current);
  }, [statoCarico]);

  // Timer Cella Frigo
  useEffect(() => {
    if (frigoAttivo) {
      frigoTimerRef.current = setInterval(() => setSecondiFrigo(prev => prev + 1), 1000);
    } else {
      clearInterval(frigoTimerRef.current);
    }
    return () => clearInterval(frigoTimerRef.current);
  }, [frigoAttivo]);

  // Geolocation
  useEffect(() => {
    if (isLogged && "geolocation" in navigator) {
      navigator.geolocation.getCurrentPosition(
        (pos) => setLocation(`${pos.coords.latitude.toFixed(6)},${pos.coords.longitude.toFixed(6)}`),
        null, { enableHighAccuracy: true }
      );
    }
  }, [isLogged]);

  const formattaTempo = (sec) => {
    const h = Math.floor(sec / 3600);
    const m = Math.floor((sec % 3600) / 60);
    const s = sec % 60;
    if (h > 0) return `${h}h ${m}m`;
    return `${m}:${s < 10 ? '0' + s : s}`;
  };

  const mostraMessaggio = (testo, tipo) => {
    setNotifica({ mostra: true, messaggio: testo, tipo: tipo });
    setTimeout(() => setNotifica({ mostra: false, messaggio: '', tipo: '' }), 4000);
  };

  const inviaDati = async (operazione, extra = {}) => {
    setInInvio(true);
    const payload = {
      autista, targa, operazione,
      posizione: location || "0,0",
      data: new Date().toLocaleDateString('it-IT'),
      ora: new Date().toLocaleTimeString('it-IT'),
      ...extra
    };
    try {
      if (GOOGLE_SCRIPT_URL) {
        await fetch(GOOGLE_SCRIPT_URL, {
          method: "POST",
          mode: "no-cors",
          headers: { 'Content-Type': 'application/json' },
          body: JSON.stringify(payload)
        });
      }
      mostraMessaggio(`${operazione.replace(/_/g, ' ')} Inviato!`, "success");
    } catch (e) {
      mostraMessaggio("Errore Connessione!", "error");
    } finally {
      setInInvio(false);
    }
  };

  const handleLogin = () => {
    if (!autista || !targa || targa.length < 5) {
      mostraMessaggio("Dati incompleti!", "error");
      return;
    }
    localStorage.setItem('sm_autista', autista);
    localStorage.setItem('sm_targa', targa.toUpperCase());
    localStorage.setItem('sm_logged', 'true');
    setIsLogged(true);
  };

  const handleLogout = () => {
    localStorage.clear();
    setIsLogged(false);
  };

  const handleFileUpload = (e) => {
    const files = Array.from(e.target.files);
    const pdfFiles = files.filter(file => file.type === 'application/pdf');
   
    if (pdfFiles.length < files.length) {
      mostraMessaggio("Sono ammessi solo file PDF!", "error");
    }

    const nuoviDocumenti = pdfFiles.map(file => ({
      name: file.name,
      size: (file.size / 1024 / 1024).toFixed(2) + ' MB',
      date: new Date().toLocaleDateString('it-IT')
    }));

    setDocumentiCaricati(prev => [...prev, ...nuoviDocumenti]);
    if (pdfFiles.length > 0) mostraMessaggio("PDF caricato correttamente!", "success");
  };

  const rimuoviDoc = (index) => {
    setDocumentiCaricati(prev => prev.filter((_, i) => i !== index));
    mostraMessaggio("Documento rimosso", "success");
  };

  // Funzioni Carburante
  const inviaCarburante = () => {
    if (!carburante.litri || !carburante.euro) {
      mostraMessaggio("Inserire Litri ed Euro!", "error");
      return;
    }
    const nuovoRecord = {
      ...carburante,
      data: new Date().toISOString(),
      ora: new Date().toLocaleTimeString('it-IT')
    };
    const nuovoStorico = [nuovoRecord, ...storicoCarburante];
    setStoricoCarburante(nuovoStorico);
    localStorage.setItem('sm_storico_carburante', JSON.stringify(nuovoStorico));
   
    inviaDati("RIFORNIMENTO", { litri: carburante.litri, euro: carburante.euro });
    setCarburante({ litri: '', euro: '' });
  };

  const calcolaConsumoGiornaliero = () => {
    if (storicoCarburante.length < 2) return { litri: 0, euro: 0 };
   
    const ultimo = new Date(storicoCarburante[0].data);
    const primo = new Date(storicoCarburante[storicoCarburante.length - 1].data);
    const diffGiorni = Math.max(1, Math.ceil(Math.abs(ultimo - primo) / (1000 * 60 * 60 * 24)));
   
    const totaliLitri = storicoCarburante.reduce((acc, curr) => acc + parseFloat(curr.litri || 0), 0);
    const totaliEuro = storicoCarburante.reduce((acc, curr) => acc + parseFloat(curr.euro || 0), 0);
   
    return {
      litri: (totaliLitri / diffGiorni).toFixed(2),
      euro: (totaliEuro / diffGiorni).toFixed(2)
    };
  };

  const renderOperativo = () => (
    <div className="space-y-6">
      <div className="p-6 rounded-[2.5rem] shadow-xl border border-white/5" style={{ backgroundColor: COLORS.surface }}>
        <div className="flex items-center justify-between mb-6">
          <div className="flex items-center gap-2">
            <div className="p-2 rounded-xl text-white" style={{ backgroundColor: COLORS.primary }}>
              <Download size={18} />
            </div>
            <h3 className="text-[10px] font-black uppercase tracking-widest" style={{ color: COLORS.text }}>1. Gestione Carico</h3>
          </div>
          {statoCarico === 'in_corso' && (
            <span className="flex items-center gap-1.5 text-xs font-black animate-pulse" style={{ color: COLORS.primary }}>
              <Clock size={14} /> {formattaTempo(secondi)}
            </span>
          )}
        </div>
        <div className="space-y-4">
          <input
            type="text" placeholder="NUMERO DISTINTA"
            className="w-full p-5 rounded-2xl font-black border-2 outline-none text-center text-xl uppercase tracking-widest shadow-inner transition-all"
            style={{ backgroundColor: COLORS.bg, borderColor: COLORS.primary + '33', color: COLORS.primary }}
            value={nDistinta}
            onChange={(e)=>setNDistinta(e.target.value)}
            disabled={statoCarico === 'in_corso'}
          />
          {statoCarico === 'fermo' ? (
            <button
              onClick={() => { if(!nDistinta) return; setStatoCarico('in_corso'); setSecondi(0); inviaDati("INIZIO_CARICO", { distinta: nDistinta }); }}
              disabled={!nDistinta}
              className={`w-full flex items-center justify-center gap-3 p-6 rounded-3xl font-black text-sm uppercase shadow-lg transition-all ${nDistinta ? 'text-white' : 'opacity-30'}`}
              style={{ backgroundColor: nDistinta ? COLORS.primary : COLORS.muted }}
            >
              <Play size={18} fill="currentColor" /> Inizia Caricamento
            </button>
          ) : (
            <button onClick={() => {
              const durata = formattaTempo(secondi);
              const oraConclusione = new Date().toLocaleTimeString('it-IT', { hour: '2-digit', minute: '2-digit' });
             
              const nuovaVoce = {
                distinta: nDistinta,
                durata: durata,
                ora: oraConclusione,
                data: new Date().toLocaleDateString('it-IT')
              };
              const nuovaCronologia = [nuovaVoce, ...cronologiaDistinte].slice(0, 5);
              setCronologiaDistinte(nuovaCronologia);
              localStorage.setItem('sm_cronologia_distinte', JSON.stringify(nuovaCronologia));

              inviaDati("FINE_CARICO", { distinta: nDistinta, durata: durata });
              setStatoCarico('fermo'); setNDistinta('');
            }} className="w-full flex items-center justify-center gap-3 p-6 bg-red-600 text-white rounded-3xl font-black text-sm uppercase shadow-xl active:scale-95 transition-all">
              <Square size={18} fill="currentColor" /> Concludi Carico
            </button>
          )}
        </div>

        {cronologiaDistinte.length > 0 && (
          <div className="mt-8 pt-6 border-t border-white/5">
            <div className="flex items-center gap-2 mb-4">
              <History size={14} style={{ color: COLORS.muted }} />
              <h4 className="text-[9px] font-black uppercase tracking-widest" style={{ color: COLORS.muted }}>Cronologia Recente</h4>
            </div>
            <div className="space-y-2">
              {cronologiaDistinte.map((item, idx) => (
                <div key={idx} className="flex items-center justify-between p-3 rounded-xl border border-white/5" style={{ backgroundColor: COLORS.bg }}>
                   <div>
                     <p className="text-[10px] font-black text-white uppercase tracking-tighter">Dist. {item.distinta}</p>
                     <p className="text-[8px] font-bold" style={{ color: COLORS.muted }}>Ore {item.ora}</p>
                   </div>
                   <div className="text-right">
                     <p className="text-[10px] font-black" style={{ color: COLORS.primary }}>{item.durata}</p>
                   </div>
                </div>
              ))}
            </div>
          </div>
        )}
      </div>

      <div className="p-6 rounded-[2.5rem] shadow-xl border border-white/5" style={{ backgroundColor: COLORS.surface }}>
        <div className="flex items-center gap-2 mb-6">
          <div className="p-2 rounded-xl text-white" style={{ backgroundColor: COLORS.primary }}>
            <Route size={18} />
          </div>
          <h3 className="text-[10px] font-black uppercase tracking-widest" style={{ color: COLORS.text }}>2. Gestione Viaggio</h3>
        </div>
        <div className="grid grid-cols-2 gap-4 mb-4">
          <div className="space-y-1">
            <label className="text-[9px] font-black uppercase ml-2" style={{ color: COLORS.muted }}>KM Inizio</label>
            <input type="number" placeholder="00000" className="w-full p-4 rounded-2xl font-black text-center text-lg outline-none border-2" style={{ backgroundColor: COLORS.bg, borderColor: COLORS.primary + '11', color: COLORS.text }} value={kmInizio} onChange={(e)=>setKmInizio(e.target.value)} disabled={viaggioInCorso} />
          </div>
          <div className="space-y-1">
            <label className="text-[9px] font-black uppercase ml-2" style={{ color: COLORS.muted }}>KM Fine</label>
            <input type="number" placeholder="00000" className="w-full p-4 rounded-2xl font-black text-center text-lg outline-none border-2" style={{ backgroundColor: COLORS.bg, borderColor: COLORS.primary + '11', color: COLORS.text }} value={kmFine} onChange={(e)=>setKmFine(e.target.value)} disabled={!viaggioInCorso} />
          </div>
        </div>
        {!viaggioInCorso ? (
          <button onClick={() => { if(!kmInizio) return; setViaggioInCorso(true); inviaDati("INIZIO_VIAGGIO", { km_inizio: kmInizio }); }} className="w-full p-5 text-white rounded-3xl font-black text-xs uppercase shadow-lg active:scale-95 transition-all" style={{ backgroundColor: COLORS.primary }}>Inizia Viaggio</button>
        ) : (
          <button onClick={() => {
            const kmi = parseFloat(kmInizio);
            const kmf = parseFloat(kmFine);
            if(!kmFine || kmf <= kmi) {
              mostraMessaggio("KM Fine devono essere maggiori!", "error");
              return;
            }
            const totale = kmf - kmi;
            inviaDati("FINE_VIAGGIO", { km_inizio: kmi, km_fine: kmf, km_percorsi: totale });
            setViaggioInCorso(false);
            setKmInizio(''); setKmFine('');
          }} className="w-full p-5 bg-red-600 text-white rounded-3xl font-black text-xs uppercase shadow-xl active:scale-95 transition-all">Chiudi Viaggio</button>
        )}
      </div>
    </div>
  );

  const renderMezzo = () => (
    <div className="space-y-4">
      <div className="grid grid-cols-2 gap-4">
        <div className="p-4 rounded-[2rem] shadow-lg border border-white/5 flex flex-col justify-between" style={{ backgroundColor: COLORS.surface }}>
            <div className="flex items-center gap-2 mb-3">
            <Waves size={14} style={{ color: COLORS.primary }} />
            <h3 className="text-[9px] font-black uppercase" style={{ color: COLORS.text }}>Pulizia</h3>
          </div>
          <div className="space-y-2">
            <button onClick={() => inviaDati("LAVAGGIO_INTERNO")} className="w-full py-2 rounded-xl text-[8px] font-black uppercase border transition-all" style={{ backgroundColor: COLORS.bg, borderColor: COLORS.primary + '33', color: COLORS.primary }}>Interno</button>
            <button onClick={() => inviaDati("LAVAGGIO_ESTERNO")} className="w-full py-2 rounded-xl text-[8px] font-black uppercase border transition-all" style={{ backgroundColor: COLORS.bg, borderColor: COLORS.primary + '33', color: COLORS.primary }}>Esterno</button>
          </div>
        </div>
        <div className={`p-4 rounded-[2rem] shadow-lg transition-all border flex flex-col justify-between`} style={{ backgroundColor: frigoAttivo ? COLORS.primary : COLORS.surface, borderColor: 'rgba(255,255,255,0.1)' }}>
          <div className="flex items-center justify-between mb-2">
            <Thermometer size={14} style={{ color: frigoAttivo ? 'white' : COLORS.primary }} />
            {frigoAttivo && <span className="text-[8px] font-black text-white">{formattaTempo(secondiFrigo)}</span>}
          </div>
          <button
            onClick={() => {
              const nuovoStato = !frigoAttivo;
              setFrigoAttivo(nuovoStato);
              inviaDati(nuovoStato ? "ACCENSIONE_FRIGO" : "SPEGNIMENTO_FRIGO", { durata_totale: formattaTempo(secondiFrigo) });
            }}
            className={`w-full py-3 rounded-xl flex items-center justify-center gap-2 transition-all ${frigoAttivo ? 'bg-white/20 text-white' : 'text-white'}`}
            style={{ backgroundColor: !frigoAttivo ? COLORS.primary : undefined }}
          >
            <Power size={14} />
            <span className="text-[9px] font-black uppercase">{frigoAttivo ? 'Spegni' : 'Accendi'}</span>
          </button>
        </div>
      </div>

      <div className="p-6 rounded-[2.5rem] shadow-xl border border-white/5" style={{ backgroundColor: COLORS.surface }}>
        <div className="flex items-center gap-2 mb-6">
          <div className="p-2 rounded-xl text-white" style={{ backgroundColor: '#f97316' }}>
            <AlertTriangle size={18} />
          </div>
          <h3 className="text-[10px] font-black uppercase tracking-widest" style={{ color: COLORS.text }}>Segnalazione Officina</h3>
        </div>
        <div className="space-y-4">
          <select className="w-full p-4 rounded-2xl border-2 font-bold text-xs outline-none" style={{ backgroundColor: COLORS.bg, borderColor: 'rgba(255,255,255,0.1)', color: COLORS.text }} value={guasto.componente} onChange={(e)=>setGuasto({...guasto, componente: e.target.value})}>
            <option value="">Seleziona componente...</option>
            <option value="Motore">Motore / Meccanica</option>
            <option value="Freni">Sistema Frenante</option>
            <option value="Luci">Luci / Fari</option>
            <option value="Gomme">Pneumatici</option>
            <option value="Sponda">Sponda Caricatrice</option>
            <option value="Frigo">Guasto Cella Frigo</option>
          </select>
          <textarea placeholder="Descrivi il problema riscontrato..." className="w-full p-4 rounded-2xl border-2 font-bold text-xs h-24 outline-none transition-all" style={{ backgroundColor: COLORS.bg, borderColor: 'rgba(255,255,255,0.1)', color: COLORS.text }} value={guasto.descrizione} onChange={(e)=>setGuasto({...guasto, descrizione: e.target.value})}></textarea>
          <button onClick={()=>inviaDati("SEGNALAZIONE_GUASTO", guasto)} className="w-full p-5 bg-orange-600 text-white rounded-3xl font-black text-xs uppercase shadow-lg">Invia Segnalazione</button>
        </div>
      </div>
    </div>
  );

  const renderCarburante = () => {
    const consumo = calcolaConsumoGiornaliero();
    return (
      <div className="space-y-6">
        <div className="grid grid-cols-2 gap-4">
           <div className="p-5 rounded-[2rem] border border-white/5 shadow-xl" style={{ backgroundColor: COLORS.surface }}>
              <p className="text-[9px] font-black uppercase text-emerald-500 mb-1">Litri / Giorno</p>
              <h4 className="text-xl font-black text-white">{consumo.litri} <span className="text-[10px] opacity-50">L</span></h4>
           </div>
           <div className="p-5 rounded-[2rem] border border-white/5 shadow-xl" style={{ backgroundColor: COLORS.surface }}>
              <p className="text-[9px] font-black uppercase text-blue-400 mb-1">Spesa / Giorno</p>
              <h4 className="text-xl font-black text-white">{consumo.euro} <span className="text-[10px] opacity-50">€</span></h4>
           </div>
        </div>

        <div className="p-6 rounded-[2.5rem] shadow-xl border border-white/5" style={{ backgroundColor: COLORS.surface }}>
          <div className="flex items-center gap-2 mb-6">
            <div className="p-2 rounded-xl text-white" style={{ backgroundColor: '#059669' }}>
              <Fuel size={18} />
            </div>
            <h3 className="text-[10px] font-black uppercase tracking-widest" style={{ color: COLORS.text }}>Rifornimento Carburante</h3>
          </div>
         
          <div className="space-y-4">
            <div className="grid grid-cols-2 gap-4">
              <div className="space-y-2">
                <label className="text-[9px] font-black uppercase ml-2" style={{ color: COLORS.muted }}>Litri Immessi</label>
                <input type="number" step="0.01" placeholder="0.00" className="w-full p-5 rounded-2xl border outline-none font-black text-white text-center text-lg" style={{ backgroundColor: COLORS.bg, borderColor: 'rgba(255,255,255,0.05)' }} value={carburante.litri} onChange={(e)=>setCarburante({...carburante, litri: e.target.value})} />
              </div>
              <div className="space-y-2">
                <label className="text-[9px] font-black uppercase ml-2" style={{ color: COLORS.muted }}>Totale Euro</label>
                <input type="number" step="0.01" placeholder="0.00" className="w-full p-5 rounded-2xl border outline-none font-black text-white text-center text-lg" style={{ backgroundColor: COLORS.bg, borderColor: 'rgba(255,255,255,0.05)' }} value={carburante.euro} onChange={(e)=>setCarburante({...carburante, euro: e.target.value})} />
              </div>
            </div>

            <button onClick={inviaCarburante} className="w-full p-5 text-white rounded-3xl font-black text-xs uppercase shadow-lg active:scale-95 transition-all flex items-center justify-center gap-3" style={{ backgroundColor: '#059669' }}>
               <Download size={16} /> Invia Dati Carburante
            </button>
          </div>

          {storicoCarburante.length > 0 && (
            <div className="mt-8 pt-6 border-t border-white/5">
              <h4 className="text-[9px] font-black uppercase tracking-widest mb-4" style={{ color: COLORS.muted }}>Ultimi Rifornimenti</h4>
              <div className="space-y-2">
                {storicoCarburante.slice(0, 3).map((item, idx) => (
                  <div key={idx} className="flex items-center justify-between p-3 rounded-xl border border-white/5" style={{ backgroundColor: COLORS.bg }}>
                    <div>
                      <p className="text-[10px] font-black text-white uppercase">{new Date(item.data).toLocaleDateString('it-IT')}</p>
                      <p className="text-[8px] font-bold" style={{ color: COLORS.muted }}>Ore {item.ora}</p>
                    </div>
                    <div className="text-right">
                      <p className="text-[10px] font-black text-emerald-500">{item.litri}L / {item.euro}€</p>
                    </div>
                  </div>
                ))}
              </div>
            </div>
          )}
        </div>
      </div>
    );
  };

  const renderDocumenti = () => (
    <div className="space-y-6">
      <div className="p-6 rounded-[2.5rem] shadow-xl border border-white/5" style={{ backgroundColor: COLORS.surface }}>
        <div className="flex items-center gap-2 mb-6">
          <div className="p-2 rounded-xl text-white" style={{ backgroundColor: COLORS.primary }}>
            <Upload size={18} />
          </div>
          <h3 className="text-[10px] font-black uppercase tracking-widest" style={{ color: COLORS.text }}>Documenti PDF</h3>
        </div>

        <div
          onClick={() => fileInputRef.current.click()}
          className="w-full p-10 border-2 border-dashed rounded-3xl flex flex-col items-center justify-center gap-4 cursor-pointer hover:bg-white/5 transition-all mb-6"
          style={{ borderColor: COLORS.primary + '44', backgroundColor: COLORS.bg }}
        >
          <div className="p-4 rounded-full" style={{ backgroundColor: COLORS.primary + '11' }}>
            <File size={32} style={{ color: COLORS.primary }} />
          </div>
          <div className="text-center">
            <p className="text-xs font-black uppercase" style={{ color: COLORS.text }}>Seleziona File PDF</p>
            <p className="text-[9px] font-bold mt-1" style={{ color: COLORS.muted }}>Clicca per esplorare</p>
          </div>
          <input type="file" ref={fileInputRef} onChange={handleFileUpload} accept="application/pdf" multiple className="hidden" />
        </div>

        <div className="space-y-3">
          {documentiCaricati.length === 0 ? (
            <p className="text-[10px] text-center font-bold italic" style={{ color: COLORS.muted }}>Nessun documento caricato</p>
          ) : (
            documentiCaricati.map((doc, i) => (
              <div key={i} className="flex items-center justify-between p-4 rounded-2xl border" style={{ backgroundColor: COLORS.bg, borderColor: 'rgba(255,255,255,0.05)' }}>
                <div className="flex items-center gap-3 overflow-hidden">
                   <div className="p-2 rounded-lg" style={{ backgroundColor: COLORS.primary + '11' }}>
                      <FileText size={16} style={{ color: COLORS.primary }} />
                   </div>
                   <div className="truncate">
                      <p className="text-[10px] font-black uppercase truncate max-w-[150px]" style={{ color: COLORS.text }}>{doc.name}</p>
                      <p className="text-[8px] font-bold" style={{ color: COLORS.muted }}>{doc.size} • {doc.date}</p>
                   </div>
                </div>
                <button onClick={() => rimuoviDoc(i)} className="p-2 rounded-xl hover:bg-red-500/10 transition-all text-red-500">
                  <Trash2 size={16} />
                </button>
              </div>
            ))
          )}
        </div>
      </div>

      <div className="p-6 rounded-[2.5rem] shadow-xl border border-white/5" style={{ backgroundColor: COLORS.surface }}>
        <h3 className="text-[10px] font-black uppercase mb-4 tracking-widest" style={{ color: COLORS.muted }}>Scadenze Personali & Mezzo</h3>
        {[
          { label: 'Assicurazione', scadenza: '31/12/2025', stato: 'ok' },
          { label: 'Revisione', scadenza: '15/06/2025', stato: 'ok' },
          { label: 'Patente', scadenza: '24/11/2026', stato: 'ok' },
          { label: 'CQC', scadenza: '12/03/2025', stato: 'warning' },
          { label: 'ADR', scadenza: '05/09/2027', stato: 'ok' },
        ].map((doc, i) => (
          <div key={i} className="flex items-center justify-between p-4 mb-2 rounded-2xl border" style={{ backgroundColor: COLORS.bg, borderColor: 'rgba(255,255,255,0.05)' }}>
            <div>
              <p className="text-xs font-black uppercase" style={{ color: COLORS.text }}>{doc.label}</p>
              <p className="text-[10px] font-bold" style={{ color: COLORS.muted }}>Scade: {doc.scadenza}</p>
            </div>
            <div className={`h-2 w-2 rounded-full ${doc.stato === 'ok' ? 'bg-emerald-500' : 'bg-orange-500 animate-pulse'}`} />
          </div>
        ))}
      </div>
    </div>
  );

  const renderAssenze = () => (
    <div className="space-y-6">
      <div className="p-6 rounded-[2.5rem] shadow-xl border border-white/5" style={{ backgroundColor: COLORS.surface }}>
        <div className="flex items-center gap-2 mb-6">
          <div className="p-2 rounded-xl text-white" style={{ backgroundColor: COLORS.primary }}>
            <Calendar size={18} />
          </div>
          <h3 className="text-[10px] font-black uppercase tracking-widest" style={{ color: COLORS.text }}>Richiesta Assenza</h3>
        </div>
        <div className="space-y-4">
          <div className="grid grid-cols-2 gap-2">
            {['ferie', 'permesso', '104', 'malattia'].map(t => (
              <button key={t} onClick={()=>setAssenza({...assenza, tipo: t})} className={`p-3 rounded-xl text-[10px] font-black uppercase transition-all ${assenza.tipo === t ? 'text-white shadow-lg' : 'opacity-50'}`} style={{ backgroundColor: assenza.tipo === t ? COLORS.primary : COLORS.bg, color: assenza.tipo === t ? 'white' : COLORS.text }}>{t}</button>
            ))}
          </div>
          <div className="grid grid-cols-2 gap-4">
            <div className="space-y-1">
              <label className="text-[9px] font-black uppercase ml-2" style={{ color: COLORS.muted }}>Dal</label>
              <input type="date" className="w-full p-4 rounded-2xl border-2 font-bold text-xs" style={{ backgroundColor: COLORS.bg, borderColor: 'rgba(255,255,255,0.1)', color: COLORS.text }} value={assenza.dal} onChange={(e)=>setAssenza({...assenza, dal: e.target.value})} />
            </div>
            <div className="space-y-1">
              <label className="text-[9px] font-black uppercase ml-2" style={{ color: COLORS.muted }}>Al</label>
              <input type="date" className="w-full p-4 rounded-2xl border-2 font-bold text-xs" style={{ backgroundColor: COLORS.bg, borderColor: 'rgba(255,255,255,0.1)', color: COLORS.text }} value={assenza.al} onChange={(e)=>setAssenza({...assenza, al: e.target.value})} />
            </div>
          </div>
          <button onClick={()=>inviaDati("RICHIESTA_ASSENZA", assenza)} className="w-full p-5 text-white rounded-3xl font-black text-xs uppercase shadow-lg active:scale-95" style={{ backgroundColor: COLORS.primary }}>Invia Richiesta</button>
        </div>
      </div>
    </div>
  );

  if (!isLogged) {
    return (
      <div className="min-h-screen flex flex-col items-center justify-center p-6" style={{ backgroundColor: COLORS.bg }}>
        <div className="w-full max-w-sm space-y-8">
          <div className="text-center">
            <h1 className="text-4xl font-black italic" style={{ color: COLORS.primary }}>SAN MARTINO</h1>
            <p className="text-[10px] font-bold uppercase tracking-[0.2em] mt-2" style={{ color: COLORS.muted }}>Logistica & Trasporti</p>
          </div>
          <div className="p-8 rounded-[2.5rem] shadow-2xl border border-white/5 space-y-6" style={{ backgroundColor: COLORS.surface }}>
            <div className="space-y-2">
              <label className="text-[10px] font-black uppercase ml-2" style={{ color: COLORS.muted }}>Personale</label>
              <select className="w-full p-4 rounded-2xl border outline-none font-bold text-white" style={{ backgroundColor: COLORS.bg, borderColor: 'rgba(255,255,255,0.1)' }} value={autista} onChange={(e) => setAutista(e.target.value)}>
                <option value="">Seleziona Autista...</option>
                {elencoAutisti.map(a => <option key={a} value={a}>{a}</option>)}
              </select>
            </div>
            <div className="space-y-2">
              <label className="text-[10px] font-black uppercase ml-2" style={{ color: COLORS.muted }}>Automezzo</label>
              <input type="text" placeholder="TARGA" className="w-full p-4 rounded-2xl border outline-none uppercase font-black text-white" style={{ backgroundColor: COLORS.bg, borderColor: 'rgba(255,255,255,0.1)' }} value={targa} onChange={(e) => setTarga(e.target.value)} />
            </div>
            <button onClick={handleLogin} className="w-full text-white p-5 rounded-2xl font-black uppercase text-sm shadow-lg active:scale-95 transition-all" style={{ backgroundColor: COLORS.primary }}>Inizia Turno</button>
          </div>
        </div>
      </div>
    );
  }

  return (
    <div className="min-h-screen pb-24 text-white font-sans" style={{ backgroundColor: COLORS.bg }}>
      {/* Header */}
      <div className="p-6 sticky top-0 z-10 backdrop-blur-md border-b border-white/5" style={{ backgroundColor: 'rgba(17,16,17,0.8)' }}>
        <div className="flex items-center justify-between">
          <div>
            <h2 className="text-[9px] font-black uppercase opacity-50 tracking-widest">In Servizio</h2>
            <p className="text-sm font-black italic" style={{ color: COLORS.primary }}>{autista}</p>
          </div>
          <div className="text-right">
            <h2 className="text-[9px] font-black uppercase opacity-50 tracking-widest">Mezzo</h2>
            <p className="text-sm font-black">{targa}</p>
          </div>
          <button onClick={handleLogout} className="p-3 rounded-full bg-white/5 text-white/50 hover:text-red-500 transition-colors">
            <LogOut size={18} />
          </button>
        </div>
      </div>

      {/* Main Content */}
      <div className="max-w-md mx-auto p-6">
        {tab === 'operativo' && renderOperativo()}
        {tab === 'mezzo' && renderMezzo()}
        {tab === 'carburante' && renderCarburante()}
        {tab === 'documenti' && renderDocumenti()}
        {tab === 'assenze' && renderAssenze()}
      </div>

      {/* Navigation */}
      <div className="fixed bottom-0 left-0 right-0 p-4 pb-6 z-20">
        <div className="max-w-md mx-auto flex items-center justify-around p-3 rounded-[2.5rem] border border-white/5 shadow-2xl backdrop-blur-xl" style={{ backgroundColor: 'rgba(28,27,28,0.9)' }}>
          {[
            { id: 'operativo', icon: Truck },
            { id: 'mezzo', icon: Wrench },
            { id: 'carburante', icon: Fuel },
            { id: 'documenti', icon: FileText },
            { id: 'assenze', icon: CalendarDays }
          ].map(({ id, icon: Icon }) => (
            <button
              key={id}
              onClick={() => setTab(id)}
              className={`p-4 rounded-2xl transition-all duration-300 ${tab === id ? 'text-white scale-110' : 'text-white/30'}`}
              style={{ backgroundColor: tab === id ? COLORS.primary : 'transparent' }}
            >
              <Icon size={20} />
            </button>
          ))}
        </div>
      </div>

      {/* Notifications */}
      {notifica.mostra && (
        <div className="fixed top-24 left-1/2 -translate-x-1/2 z-50 animate-bounce">
          <div className={`px-6 py-3 rounded-2xl flex items-center gap-2 shadow-2xl border border-white/10 ${notifica.tipo === 'success' ? 'bg-emerald-600' : 'bg-red-600'}`}>
            {notifica.tipo === 'success' ? <CheckCircle2 size={16} /> : <AlertTriangle size={16} />}
            <span className="text-[10px] font-black uppercase tracking-widest">{notifica.messaggio}</span>
          </div>
        </div>
      )}

      {/* Loading Overlay */}
      {inInvio && (
        <div className="fixed inset-0 z-[100] flex items-center justify-center bg-black/80 backdrop-blur-sm">
          <div className="flex flex-col items-center gap-4">
            <RefreshCw className="animate-spin text-white" size={32} style={{ color: COLORS.primary }} />
            <p className="text-[10px] font-black uppercase tracking-[0.3em]" style={{ color: COLORS.primary }}>Invio Dati...</p>
          </div>
        </div>
      )}
    </div>
  );
};

export default App;
