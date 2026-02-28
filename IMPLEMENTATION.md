# CoverComposer (Saregama) 🎵

An AI-powered music generation web application with real-time audio synthesis, visualization, and multi-layer composition control.

## Features

### 🎹 AI Music Generation
- **Real-time Audio Synthesis**: Powered by Tone.js for browser-based music generation
- **Parameter-Driven Composition**: Control emotion intensity, key, scale, tempo, and color mood
- **Genre Fusion**: Blend two genres (Pop, Rock, Jazz, Electronic) for unique hybrid styles
- **Multi-Layer Audio**: Independent control over melody, harmony, bass, and drums

### 🎨 Interactive Controls
- **Emotion Intensity Slider**: From calm (😌) to intense (🔥)
- **Mood-to-Color Picker**: Visual color wheel that influences chord progressions
- **Key & Scale Selector**: Choose from all 12 keys and major/minor scales
- **Tempo Control**: 60-180 BPM range
- **Layer Toggles**: Enable/disable individual audio layers
- **Volume Sliders**: Per-layer volume control

### 📊 Real-Time Visualization
- **Animated Waveform Display**: Responds to actual audio playback
- **Floating Musical Symbols**: Animated background with parallax effect
- **Smart Harmony Engine**: Displays current chord progression (I-V-vi-IV)
- **Drum Pattern Visualizer**: Visual representation of kick, snare, and hi-hats

### 💾 Database Integration
- **Track History**: All generated tracks saved to Supabase
- **Search & Filter**: Find tracks by title, genre, or parameters
- **Delete Management**: Remove unwanted tracks
- **User Preferences**: Save favorite parameters and settings

### 🎼 Additional Features
- **Trending Songs**: Browse popular tracks with mock Spotify integration
- **Remix Mode**: Upload MIDI files for remixing
- **BGM Extraction**: Remove vocals from songs (UI ready)
- **Instrument Analysis**: Detect and play individual instruments (UI ready)
- **Mashup Creator**: Combine up to 5 tracks (UI ready)
- **Evolution Mode**: Generate variations and evolve compositions
- **Export Options**: MIDI, MP3, and Stems export (UI ready)

## Technology Stack

### Frontend
- **React 18** with TypeScript
- **Tailwind CSS** for styling
- **shadcn/ui** component library
- **React Router** for navigation
- **Tone.js** for audio synthesis and playback

### Backend
- **Supabase** for database and storage
- **PostgreSQL** for data persistence
- **Row Level Security** for data protection

### Audio Engine
- **Tone.js**: Web Audio API wrapper for synthesis
- **PolySynth**: Melody and harmony generation
- **MembraneSynth**: Drum synthesis
- **MetalSynth**: Hi-hat synthesis
- **Waveform Analyzer**: Real-time visualization

## Project Structure

```
src/
├── components/
│   ├── generate/
│   │   ├── ParametersPanel.tsx      # Left sidebar controls
│   │   ├── CentralVisualizer.tsx    # Waveform display
│   │   ├── LayersPanel.tsx          # Right sidebar layers
│   │   ├── ColorPicker.tsx          # Color wheel selector
│   │   └── GenreFusionCard.tsx      # Genre selection cards
│   ├── layouts/
│   │   ├── MainLayout.tsx           # App wrapper
│   │   ├── Navigation.tsx           # Top navigation bar
│   │   └── BottomPlayerBar.tsx      # Playback controls
│   ├── modals/
│   │   ├── TrendingSongsModal.tsx   # Spotify trending
│   │   ├── RemixModeModal.tsx       # MIDI upload
│   │   ├── BGMModal.tsx             # BGM extraction
│   │   ├── InstrumentsModal.tsx     # Instrument analysis
│   │   └── MashupModal.tsx          # Track mashup
│   └── ui/                          # shadcn/ui components
├── pages/
│   ├── HomePage.tsx                 # Landing page
│   ├── GeneratePage.tsx             # Main generation interface
│   ├── HistoryPage.tsx              # Track history
│   ├── EvolutionPage.tsx            # Evolution mode
│   └── ProfilePage.tsx              # User statistics
├── services/
│   ├── musicGenerator.ts            # Core audio generation
│   ├── audioVisualizer.ts           # Waveform visualization
│   └── spotifyService.ts            # Trending songs data
├── db/
│   ├── api.ts                       # Supabase API functions
│   └── supabase.ts                  # Supabase client
└── types/
    ├── types.ts                     # TypeScript interfaces
    └── index.ts                     # Type exports
```

## Database Schema

### Tables
- **tracks**: Generated music tracks with parameters
- **user_preferences**: User settings and favorites
- **evolution_history**: Track evolution genealogy
- **mashups**: Combined track records

### Storage
- **music_files**: Bucket for uploaded MIDI and audio files

## Music Generation Algorithm

### Melody Generation
1. Select scale notes based on key and scale (major/minor)
2. Generate random note sequence within scale
3. Apply emotion intensity to determine note range
4. Create 4-bar melody pattern

### Harmony Generation
1. Use common chord progressions (I-V-vi-IV for major, i-v-VI-III for minor)
2. Build triads from scale degrees
3. Synchronize with melody rhythm

### Bass Generation
1. Use root notes from chord progression
2. Octave lower than melody
3. Quarter note rhythm pattern

### Drum Generation
1. Kick on beats 1 and 3
2. Snare on beats 2 and 4
3. Hi-hats on eighth notes
4. Genre-specific variations

## Color Mood System

The color picker influences chord selection:
- **Warm colors** (red, orange, yellow) → Major chords, happy mood
- **Cool colors** (blue, purple, cyan) → Minor chords, melancholic mood

## Genre Instrument Mapping

| Genre | Synth Type | Bass Type | Drum Style |
|-------|-----------|-----------|------------|
| Pop | Sine | Triangle | Standard |
| Rock | Sawtooth | Square | Rock |
| Jazz | Sine | Sine | Jazz |
| Electronic | Square | Sawtooth | Electronic |

## Getting Started

### Prerequisites
- Node.js 18+
- pnpm package manager

### Installation
```bash
# Install dependencies
pnpm install

# Start development server
pnpm dev
```

### Environment Variables
```env
VITE_SUPABASE_URL=your_supabase_url
VITE_SUPABASE_ANON_KEY=your_supabase_anon_key
```

## Usage

### Generate Music
1. Navigate to the **Generate** page
2. Adjust parameters:
   - Emotion intensity slider
   - Color mood picker
   - Key and scale selectors
   - Genre A and Genre B
   - Tempo slider
3. Click **GENERATE MAGIC**
4. Use playback controls to listen
5. Toggle layers on/off
6. Adjust individual layer volumes
7. Export or share your creation

### View History
1. Navigate to **History** page
2. Browse all generated tracks
3. Search by title or genre
4. Play, download, or delete tracks

### Evolution Mode
1. Navigate to **Evolution** page
2. Generate three variations
3. Select your favorite
4. Click **Evolve Further** for new variations
5. Repeat to refine composition

## Design System

### Colors
- **Primary (Gold)**: `hsl(45, 100%, 51%)` - #FFD700
- **Secondary (Navy)**: `hsl(220, 100%, 15%)`
- **Accent (Cyan)**: `hsl(180, 100%, 50%)` - #00F0FF
- **Accent (Purple)**: `hsl(280, 70%, 60%)`
- **Background**: `hsl(0, 0%, 4%)` - Deep black

### Animations
- **Float**: Vertical floating motion (3s)
- **Wobble**: Rotation wobble effect (0.5s)
- **Pulse Glow**: Pulsing glow effect (2s)

## Performance Considerations

- Audio context initialized on user interaction (Tone.start())
- Waveform data updated at 10 FPS for smooth visualization
- Database queries limited to 50 most recent tracks
- Lazy loading for modal components

## Browser Compatibility

- Chrome 90+
- Firefox 88+
- Safari 14+
- Edge 90+

Requires Web Audio API support.

## Future Enhancements

- [ ] Three.js 3D musical symbol physics
- [ ] Real Spotify API integration
- [ ] Actual BGM vocal removal processing
- [ ] ML-based instrument recognition
- [ ] Real mashup audio processing
- [ ] MIDI file export functionality
- [ ] MP3 audio export with encoding
- [ ] User authentication system
- [ ] Social sharing features
- [ ] Collaborative composition mode

## License

MIT License - See LICENSE file for details

## Credits

- **Tone.js**: Audio synthesis library
- **shadcn/ui**: Component library
- **Supabase**: Backend infrastructure
- **Tailwind CSS**: Styling framework

---

Built with ❤️ using React, TypeScript, and Tone.js
