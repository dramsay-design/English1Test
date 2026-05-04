<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Ms. Clarke's English One Test</title>
  <style>
    :root{
      --coral:#ff6f91;
      --orange:#ff9671;
      --magenta:#d65db1;
      --mint:#98ffdc;
      --deep:#3b1232;
      --card:#fff7fb;
      --soft:#ffe5ef;
      --shadow:0 18px 45px rgba(59,18,50,.22);
    }
    *{box-sizing:border-box;}
    body{
      margin:0;
      font-family:Arial, Helvetica, sans-serif;
      color:var(--deep);
      background:linear-gradient(135deg,var(--coral),var(--orange),var(--magenta));
      min-height:100vh;
      overflow-x:hidden;
      user-select:none;
    }
    body::before{
      content:"";
      position:fixed;
      inset:0;
      background:
        radial-gradient(circle at 10% 20%, rgba(152,255,220,.7), transparent 18%),
        radial-gradient(circle at 90% 12%, rgba(255,255,255,.35), transparent 15%),
        radial-gradient(circle at 50% 95%, rgba(152,255,220,.45), transparent 18%);
      pointer-events:none;
      animation:floatGlow 9s ease-in-out infinite alternate;
    }
    @keyframes floatGlow{from{transform:translateY(0)}to{transform:translateY(-18px)}}
    .sparkle{
      position:fixed;
      width:10px;height:10px;border-radius:50%;
      background:rgba(255,255,255,.7);
      animation:rise 7s linear infinite;
      pointer-events:none;
    }
    @keyframes rise{0%{transform:translateY(100vh) scale(.4);opacity:0}20%{opacity:1}100%{transform:translateY(-10vh) scale(1.1);opacity:0}}
    .app{position:relative;z-index:1;max-width:1120px;margin:0 auto;padding:24px;}
    .screen{display:none;animation:fadeIn .45s ease;}
    .screen.active{display:block;}
    @keyframes fadeIn{from{opacity:0;transform:translateY(14px)}to{opacity:1;transform:translateY(0)}}
    .hero,.card{
      background:rgba(255,247,251,.94);
      border:3px solid rgba(255,255,255,.55);
      border-radius:28px;
      box-shadow:var(--shadow);
      padding:28px;
      backdrop-filter:blur(8px);
    }
    .hero{text-align:center;margin-top:42px;}
    h1{font-size:clamp(2.2rem,5vw,4.5rem);margin:.2rem 0;color:#8b145f;text-shadow:2px 3px 0 rgba(152,255,220,.55)}
    h2{font-size:1.85rem;margin:0 0 12px;color:#9b176d;}
    h3{margin:16px 0 8px;color:#7d1157;}
    p,li{line-height:1.55;font-size:1rem;}
    .subtitle{font-size:1.2rem;font-weight:700;}
    input[type="text"]{
      width:min(440px,100%);
      padding:16px 18px;
      border:3px solid var(--magenta);
      border-radius:18px;
      font-size:1.1rem;
      outline:none;
      background:white;
      color:var(--deep);
    }
    button{
      border:0;
      border-radius:18px;
      padding:14px 20px;
      margin:8px 5px;
      background:linear-gradient(135deg,var(--magenta),var(--coral),var(--orange));
      color:white;
      font-weight:800;
      font-size:1rem;
      cursor:pointer;
      box-shadow:0 8px 18px rgba(59,18,50,.24);
      transition:transform .2s, box-shadow .2s;
    }
    button:hover{transform:translateY(-2px);box-shadow:0 12px 24px rgba(59,18,50,.28)}
    button.secondary{background:linear-gradient(135deg,#35cba2,var(--mint));color:#2f1230;}
    .topbar{display:flex;gap:14px;align-items:center;justify-content:space-between;margin-bottom:18px;flex-wrap:wrap;}
    .pill{background:rgba(152,255,220,.55);padding:10px 14px;border-radius:999px;font-weight:800;}
    .progress{height:18px;background:rgba(255,255,255,.6);border-radius:999px;overflow:hidden;flex:1;min-width:220px;border:2px solid rgba(255,255,255,.8)}
    .progressFill{height:100%;width:0%;background:linear-gradient(90deg,var(--mint),var(--orange),var(--magenta));transition:.3s;}
    .layout{display:grid;grid-template-columns:1fr 1fr;gap:18px;}
    .passage,.questionBox{background:white;border-radius:22px;padding:20px;box-shadow:0 8px 22px rgba(59,18,50,.12);max-height:70vh;overflow:auto;}
    .passage{border-left:8px solid var(--mint);}
    .smallNote{font-size:.9rem;background:var(--soft);padding:10px 12px;border-radius:14px;font-weight:700;}
    .option{
      display:block;
      width:100%;
      text-align:left;
      background:#fff4fa;
      border:2px solid #f5b3d8;
      border-radius:16px;
      padding:12px 14px;
      margin:10px 0;
      cursor:pointer;
      font-weight:700;
    }
    .option.selected{background:rgba(152,255,220,.45);border-color:#36cfa4;}
    .blankInput{width:100%;margin-top:8px;}
    .dragArea,.dropArea{display:flex;gap:10px;flex-wrap:wrap;min-height:70px;padding:12px;border-radius:16px;background:#fff2f9;border:2px dashed #d65db1;margin:10px 0;}
    .dragItem{padding:10px 12px;border-radius:14px;background:linear-gradient(135deg,var(--orange),var(--coral));color:white;font-weight:800;cursor:grab;box-shadow:0 4px 10px rgba(0,0,0,.15)}
    .dropZone{flex:1;min-width:190px;min-height:74px;background:white;border:2px solid var(--mint);border-radius:16px;padding:10px;}
    .dropZone strong{display:block;margin-bottom:6px;color:#8b145f;}
    .feedback{font-weight:800;margin-top:8px;min-height:24px;}
    .correct{color:#167a55}.incorrect{color:#9e164c}
    .navBtns{display:flex;justify-content:space-between;align-items:center;margin-top:16px;gap:12px;flex-wrap:wrap;}
    .certificate{
      background:white;
      border:10px double var(--magenta);
      border-radius:28px;
      padding:34px;
      text-align:center;
      box-shadow:var(--shadow);
    }
    .certName{font-size:2rem;color:#8b145f;font-weight:900;border-bottom:3px solid var(--mint);display:inline-block;padding:8px 30px;margin:10px;}
    .scoreBig{font-size:3rem;font-weight:900;color:#8b145f;}
    table{width:100%;border-collapse:collapse;background:white;border-radius:12px;overflow:hidden;margin-top:12px;}
    th,td{border:1px solid #f0b8d9;padding:8px;text-align:left;vertical-align:top;}
    th{background:#ffe2ef;}
    @media(max-width:850px){.layout{grid-template-columns:1fr}.passage,.questionBox{max-height:none}}
    @media print{body{background:white}.noPrint,.topbar,.navBtns{display:none!important}.certificate{box-shadow:none;border-color:#000}.app{max-width:none}}
  </style>
</head>
<body oncopy="return false" oncut="return false" onpaste="return false" oncontextmenu="return false">
  <div class="sparkle" style="left:8%;animation-delay:0s"></div><div class="sparkle" style="left:22%;animation-delay:1.5s"></div><div class="sparkle" style="left:45%;animation-delay:3s"></div><div class="sparkle" style="left:67%;animation-delay:.7s"></div><div class="sparkle" style="left:88%;animation-delay:2.2s"></div>
  <main class="app">
    <section id="home" class="screen active">
      <div class="hero">
        <h1>Ms. Clarke's English One Test</h1>
        <p class="subtitle">End-of-Year Examination • English I • RL.9 & RI.9 Standards</p>
        <p>Read carefully, analyze deeply, and trust your thinking. You are prepared for this moment. Do your best, cite the text in your mind, and choose the answer that is most precise.</p>
        <input id="studentName" type="text" placeholder="Enter your full name" autocomplete="off" />
        <br><button onclick="startTest()">Begin Test</button>
        <p class="smallNote">Copy, paste, right-click, and text selection are disabled. Questions are challenging, so read every answer choice fully.</p>
      </div>
    </section>

    <section id="test" class="screen">
      <div class="topbar noPrint">
        <span class="pill" id="studentPill">Student</span>
        <div class="progress"><div class="progressFill" id="progressFill"></div></div>
        <span class="pill" id="counter">Question 1 of 24</span>
      </div>
      <div class="layout">
        <article class="passage" id="passageBox"></article>
        <article class="questionBox" id="questionBox"></article>
      </div>
      <div class="navBtns noPrint">
        <button class="secondary" onclick="prevQuestion()">Back</button>
        <div>
          <button onclick="checkAnswer()">Submit Answer</button>
          <button class="secondary" onclick="nextQuestion()">Next</button>
        </div>
      </div>
    </section>

    <section id="results" class="screen">
      <div class="card" id="resultsBox"></div>
    </section>
  </main>
<footer style="text-align:center; padding:20px; font-weight:bold; color:white;">
Created by Dwaynna Ramsay-Morgan M.Ed.
</footer>

<script>
const passages = {
  lamb: `<h2>Short Story Excerpt: Lamb to the Slaughter</h2><p>Mary Maloney sat quietly in the living room, waiting for her husband to come home. Everything about the space reflected comfort and routine—the soft lighting, the carefully arranged furniture, and the calm rhythm of her evening. When Patrick arrived, however, something was different. His movements were sharp and distant, and his voice lacked the warmth she expected. He spoke briefly, delivering news that shattered the stability Mary had built her life around.</p><p>At first, she responded automatically, continuing to prepare dinner as if nothing had changed. Her hands moved with practiced ease, but her mind struggled to catch up with what she had just heard. The contrast between her calm actions and the emotional storm inside her created a quiet tension. As the evening unfolded, a sudden and irreversible decision was made. In the aftermath, Mary’s thoughts shifted rapidly. She began to consider what others would notice, how events might appear, and what version of the truth would seem most believable.</p><p>Her focus turned to maintaining normalcy. Every action became deliberate, not out of peace, but out of careful control. What had once been routine was now strategy, and what seemed ordinary now concealed something far more complex beneath the surface.</p>`,
  loser: `<h2>Short Story Excerpt: The Loser — Aimee Bender</h2><p>The man was known for a strange and remarkable ability—he could find things that others had lost. At first, people admired him for it. They approached him with hope, bringing stories of missing objects that carried deep emotional value. When he successfully returned these items, they praised him, treating his gift as something extraordinary.</p><p>Over time, however, their admiration shifted. Instead of seeing him as a person, they began to see him only as a solution to their problems. His identity became tied to what he could recover rather than who he was. The objects he found often carried memories, regrets, and unfinished emotions. Yet even when those objects were returned, something deeper remained unresolved.</p><p>The man began to realize that his ability did not truly fix what was broken. Instead, it exposed how much people depended on physical things to hold their sense of self. His gift, once a source of pride, became a burden. It forced him to confront the gap between what is lost physically and what is lost emotionally—a gap that could not always be filled.</p>`,
  boys: `<h2>Novel Excerpt: All American Boys</h2><p>After the incident involving Rashad and a police officer, the community was left unsettled. Stories began to spread, each shaped by who was telling them and what they believed. Rashad’s absence from school became more than just a missing student—it became a symbol of something larger. Students whispered in hallways, teachers struggled to address the tension, and the community divided in quiet but noticeable ways.</p><p>Quinn found himself caught in the middle. He had connections to the officer involved, which made the situation personal and complicated. At the same time, he could not ignore what he had witnessed. The truth seemed clear, yet speaking it aloud carried consequences. His internal conflict grew as he questioned where his loyalty should lie—with people he knew or with what he knew to be right.</p><p>As days passed, the silence surrounding the event became just as powerful as the incident itself. Some people chose not to speak, believing it was safer. Others recognized that staying quiet allowed injustice to continue. The situation forced individuals to examine their values, revealing that truth, courage, and accountability often come at a cost.</p>`,
  romeo: `<h2>Drama Excerpt: Romeo and Juliet</h2><p><strong>Romeo:</strong> But soft! What light through yonder window breaks? It is the east, and Juliet is the sun.</p><p><strong>Juliet:</strong> O Romeo, Romeo! wherefore art thou Romeo? Deny thy father and refuse thy name; Or, if thou wilt not, be but sworn my love, And I’ll no longer be a Capulet.</p><p><strong>Romeo:</strong> Shall I hear more, or shall I speak at this?</p><p><strong>Juliet:</strong> ’Tis but thy name that is my enemy; Thou art thyself, though not a Montague. What’s Montague? It is nor hand, nor foot, Nor arm, nor face, nor any other part Belonging to a man.</p>`,
  hughes: `<h2>Poem: Theme for English B by Langston Hughes</h2><p>The instructor said,</p><p style="margin-left:30px">Go home and write<br> a page tonight.<br> And let that page come out of you—<br> Then, it will be true.</p><p>I wonder if it’s that simple?<br>I am twenty-two, colored, born in Winston-Salem.<br>I went to school there, then Durham, then here<br>to this college on the hill above Harlem.<br>I am the only colored student in my class.<br>The steps from the hill lead down into Harlem,<br>through a park, then I cross St. Nicholas,<br>Eighth Avenue, Seventh, and I come to the Y,<br>the Harlem Branch Y, where I take the elevator<br>up to my room, sit down, and write this page:</p><p>It’s not easy to know what is true for you or me<br>at twenty-two, my age. But I guess I’m what<br>I feel and see and hear, Harlem, I hear you:<br>hear you, hear me—we two—you, me, talk on this page.<br>(I hear New York, too.) Me—who?<br>Well, I like to eat, sleep, drink, and be in love.<br>I like to work, read, learn, and understand life.<br>I like a pipe for a Christmas present,<br>or records—Bessie, bop, or Bach.<br>I guess being colored doesn’t make me not like<br>the same things other folks like who are other races.<br>So will my page be colored that I write?</p><p>Being me, it will not be white.<br>But it will be<br>a part of you, instructor.<br>You are white—<br>yet a part of me, as I am a part of you.<br>That’s American.<br>Sometimes perhaps you don’t want to be a part of me.<br>Nor do I often want to be a part of you.<br>But we are, that’s true!<br>As I learn from you,<br>I guess you learn from me—<br>although you’re older—and white—<br>and somewhat more free.</p><p>This is my page for English B</p>`,
  evolution: `<h2>Informational Text: Evolution isn’t random. Scientists find the same genes used for 120 million years</h2><p><strong>Date:</strong> May 4, 2026<br><strong>Source:</strong> University of York</p><p>Scientists have uncovered evidence that evolution has relied on the same genetic "cheat sheet" for more than 120 million years, raising the possibility that life on Earth may be more predictable than once believed.</p><h3>Shared Genes Behind Butterfly and Moth Mimicry</h3><p>An international group of researchers led by the University of York and the Wellcome Sanger Institute focused on butterflies and moths from South American rainforests. Although these species are only distantly related, many share strikingly similar wing color patterns that serve as warning signals to predators. This phenomenon is known as mimicry.</p><p>The researchers set out to identify which genes control these shared color patterns across seven distantly related species. Despite their evolutionary distance, the team discovered that both butterflies and moths repeatedly relied on the same two genes, <em>ivory</em> and <em>optix</em>, to produce nearly identical warning colors.</p><p>Instead of altering the genes themselves, evolution acted on regulatory elements, often described as genetic "switches," that control when and where these genes are activated. In butterflies, these switches were modified in similar ways across species. In the moth, scientists found a surprising twist. It used an inversion mechanism, a large chunk of DNA flipped backwards, that closely mirrors a strategy seen in one of the butterfly species.</p><h3>Evidence That Evolution Can Be Predictable</h3><p>Professor Kanchon Dasmahapatra from the University of York's Department of Biology explained that convergent evolution, where unrelated species independently evolve the same trait, is common across the tree of life, but scientists rarely get the opportunity to investigate the genetic basis of the phenomenon.</p><p>Investigating seven butterfly lineages and a day-flying moth, the team showed that evolution can be surprisingly predictable, and that butterflies and moths have been using the exact same genetic tricks repeatedly to achieve similar color patterns since the age of the dinosaurs.</p><p>The findings, published in <em>PLoS Biology</em>, suggest that evolution is not always a random process. Instead, it can follow recurring genetic pathways.</p><h3>Why Warning Colors Keep Reappearing</h3><p>Professor Joana Meier from the Wellcome Sanger Institute added that these distantly related butterflies and the moth are toxic and distasteful to birds. They look alike because if birds have learned that a specific pattern means "do not eat," it benefits other species to display the same warning colors.</p><p>The researchers explain that these warning colors may be particularly ideal because they seem relatively easy to evolve due to a highly conserved genetic basis over 120 million years.</p><h3>What This Means for Predicting Evolution</h3><p>Understanding that evolution often follows established genetic routes could help scientists anticipate how species may respond to changing environments or climate shifts. If nature tends to reuse the same biological solutions, predicting future adaptations may become more achievable than previously thought.</p>`
};

const questions = [
{p:'lamb',std:'RL.9.3',type:'mc',q:'Which analysis best explains how Mary’s routine actions develop her character after Patrick speaks to her?',opts:['They reveal that she is emotionally detached from Patrick and never valued the marriage.','They suggest shock because she keeps performing familiar behaviors while her inner reality has changed.','They prove she planned the entire event before Patrick entered the room.','They show that Patrick’s words have no meaningful effect on her decisions.'],ans:1},
{p:'lamb',std:'RL.9.1',type:'multi',q:'Select TWO pieces of evidence that best support the inference that Mary is trying to manage how others will perceive the situation.',opts:['She thinks about what others will notice.','She prepares dinner as part of an ordinary routine.','Patrick speaks in a flat voice.','The room had been arranged around comfort.','Her future feels broken.'],ans:[0,1]},
{p:'lamb',std:'RL.9.4',type:'blank',q:'In the line “Her calmness seems automatic rather than peaceful,” the word automatic most nearly means _____.',ans:['mechanical','unthinking','instinctive','habitual']},
{p:'lamb',std:'RL.9.5',type:'drag',q:'Drag each story element to the role it plays in creating suspense.',items:['Patrick’s distant manner','Mary’s ordinary dinner routine','Mary’s careful thinking'],zones:['Signals a disruption before the conflict is explained','Contrasts normal behavior with hidden danger','Shows a shift from shock to calculation'],ans:[0,1,2]},

{p:'loser',std:'RL.9.2',type:'mc',q:'Which theme is most strongly developed by the excerpt from “The Loser”?',opts:['A rare gift can create isolation when others value the ability more than the person.','Objects matter only because they can be sold or replaced by others.','People who lose things are always careless and emotionally immature.','Talent guarantees respect when it is used consistently to help people.'],ans:0},
{p:'loser',std:'RL.9.6',type:'mc',q:'How does the perspective in the excerpt shape the reader’s understanding of the main character?',opts:['It presents him as unreliable by showing that he lies about finding lost objects.','It emphasizes society’s view of him while also revealing the emotional cost of being useful to others.','It makes the lost objects more important than the people who search for them.','It keeps the reader from understanding why people ask him for help.'],ans:1},
{p:'loser',std:'RL.9.4',type:'blank',q:'As used in the sentence “His gift becomes both a talent and a burden,” burden most nearly means _____.',ans:['hardship','weight','responsibility','strain']},
{p:'loser',std:'RL.9.1',type:'multi',q:'Select TWO details that best support the idea that the story connects physical loss with emotional loss.',opts:['People attach hope, memory, and identity to lost objects.','The main character can find lost things.','Finding something physical does not always repair what is emotionally missing.','People admire the gift when it helps them.','The character moves through the world.'],ans:[0,2]},

{p:'boys',std:'RL.9.3',type:'mc',q:'Which statement best analyzes Quinn’s conflict in the excerpt?',opts:['He must choose between protecting personal loyalty and accepting responsibility for the truth.','He wants to become famous by speaking publicly about Rashad’s experience.','He believes Rashad caused the community conflict by staying absent from school.','He is mainly concerned with avoiding school punishment for witnessing the event.'],ans:0},
{p:'boys',std:'RL.9.2',type:'mc',q:'Which central idea about silence is developed in the excerpt?',opts:['Silence is neutral when a person does not know every detail of an event.','Silence can become a form of protection for systems that cause harm.','Silence is usually safer than public action in community conflicts.','Silence affects only the people directly involved in the original incident.'],ans:1},
{p:'boys',std:'RL.9.6',type:'multi',q:'Select TWO ways the excerpt develops point of view around the incident.',opts:['It shows that different characters interpret the same event through relationships and beliefs.','It presents the officer’s view as the only reliable account.','It reveals how community pressure influences what people are willing to admit.','It removes social context so the event seems purely individual.','It suggests that Rashad’s absence has no symbolic meaning.'],ans:[0,2]},
{p:'boys',std:'RL.9.4',type:'blank',q:'In the phrase “silence can protect unfair systems,” protect most nearly means _____.',ans:['preserve','shield','defend','maintain']},

{p:'romeo',std:'RL.9.4',type:'mc',q:'What is the effect of Romeo comparing Juliet to the sun?',opts:['It shows that Juliet represents life, beauty, and emotional light in contrast to darkness.','It proves Romeo understands the political history of the Capulet family.','It suggests Juliet is dangerous because the sun can burn those who approach it.','It reveals that Romeo’s feelings are practical rather than imaginative.'],ans:0},
{p:'romeo',std:'RL.9.2',type:'mc',q:'Which theme is most clearly developed through Juliet’s speech about names?',opts:['Family identity can create barriers that conflict with personal love.','Names are more powerful than actions in every relationship.','Young people should always reject their families to become independent.','Love succeeds only when it remains hidden from public view.'],ans:0},
{p:'romeo',std:'RL.9.5',type:'drag',q:'Drag each dramatic element to its effect in the scene.',items:['Romeo overhears Juliet','Juliet questions Romeo’s name','Romeo debates whether to speak'],zones:['Creates dramatic irony because the audience knows he is present','Develops the conflict between identity and love','Builds tension through hesitation before action'],ans:[0,1,2]},
{p:'romeo',std:'RL.9.6',type:'mc',q:'How does Juliet’s perspective differ from the family conflict surrounding her?',opts:['She sees Romeo’s personal identity as separate from the inherited name Montague.','She believes Romeo’s name should matter more than his character.','She treats the feud as a problem that cannot be questioned or resisted.','She wants Romeo to prove his love by defending his family publicly.'],ans:0},

{p:'hughes',std:'RL.9.2',type:'mc',q:'Which theme is most fully developed in “Theme for English B”?',opts:['Identity is shaped by both individual experience and shared human connection.','Education removes every difference between people from unequal backgrounds.','Truth is simple when a writer follows an instructor’s directions exactly.','Art should avoid race because race prevents honest self-expression.'],ans:0},
{p:'hughes',std:'RL.9.5',type:'mc',q:'How does the poem’s structure help develop its meaning?',opts:['The movement from assignment to self-questioning to direct address mirrors the speaker’s search for truth.','The regular rhyme scheme creates a light mood that hides the speaker’s serious concerns.','The poem’s short length proves the speaker cannot fully explain his identity.','The poem separates Harlem from the classroom so the two worlds never influence each other.'],ans:0},
{p:'hughes',std:'RL.9.4',type:'blank',q:'In the line “Being me, it will not be white,” the word white most nearly refers to _____.',ans:['dominant racial identity','the instructor’s perspective','mainstream experience','white culture']},
{p:'hughes',std:'RL.9.6',type:'multi',q:'Select TWO claims about the speaker’s point of view that are best supported by the poem.',opts:['He believes race affects his experience but does not erase shared humanity.','He believes his instructor can learn from him despite differences in age and power.','He believes personal truth is completely separate from place and history.','He believes liking music and ordinary pleasures makes racial identity meaningless.','He believes America is simple because everyone experiences freedom equally.'],ans:[0,1]},

{p:'evolution',std:'RI.9.2',type:'mc',q:'Which central idea best captures the informational text?',opts:['Scientists found that unrelated butterflies and moths repeatedly use similar genetic pathways for warning-color mimicry.','Scientists proved that all evolution can now be predicted with complete certainty.','Scientists discovered that moths and butterflies are more closely related than previously believed.','Scientists found that predators create new genes in toxic butterflies and moths.'],ans:0},
{p:'evolution',std:'RI.9.3',type:'mc',q:'How does the author develop the connection between mimicry and survival?',opts:['By explaining that similar warning colors help predators recognize toxic species and avoid eating them.','By arguing that predators intentionally teach butterflies and moths to change their genes.','By describing mimicry as a decoration that has little connection to survival.','By showing that toxic species become harmless when they share the same wing colors.'],ans:0},
{p:'evolution',std:'RI.9.5',type:'drag',q:'Drag each section idea to the role it plays in the article’s structure.',items:['Shared genes behind mimicry','Evidence evolution can be predictable','What this means for predicting evolution'],zones:['Introduces the scientific discovery and mechanism','Explains the broader claim supported by the study','Extends the finding to future environmental change'],ans:[0,1,2]},
{p:'evolution',std:'RI.9.8',type:'multi',q:'Select TWO claims that are supported by evidence in the article.',opts:['The same two genes, ivory and optix, were repeatedly involved in similar warning colors.','Evolution always produces identical results in every environment.','Regulatory switches can affect when and where genes are activated.','Birds prefer to eat toxic butterflies with bright warning colors.','The study focused only on one butterfly species from North America.'],ans:[0,2]}
];

let current=0;
let student='';
let responses=Array(questions.length).fill(null);
let locked=Array(questions.length).fill(false);
let shuffled=[];

function shuffleArray(arr){return arr.map(v=>[Math.random(),v]).sort((a,b)=>a[0]-b[0]).map(x=>x[1]);}
function startTest(){
  const name=document.getElementById('studentName').value.trim();
  if(!name){alert('Please enter your full name.');return;}
  student=name;
  shuffled=questions.map(q=>q.type==='mc'||q.type==='multi'?shuffleArray(q.opts.map((o,i)=>({text:o,orig:i}))):null);
  document.getElementById('studentPill').textContent=student;
  showScreen('test');renderQuestion();
}
function showScreen(id){document.querySelectorAll('.screen').forEach(s=>s.classList.remove('active'));document.getElementById(id).classList.add('active');}
function renderQuestion(){
  const q=questions[current];
  document.getElementById('passageBox').innerHTML=passages[q.p];
  document.getElementById('counter').textContent=`Question ${current+1} of ${questions.length}`;
  document.getElementById('progressFill').style.width=`${(current/questions.length)*100}%`;
  let html=`<h2>Question ${current+1}</h2><p class="smallNote">Standard: ${q.std} • DOK 3–4</p><h3>${q.q}</h3>`;
  if(q.type==='mc'){
    shuffled[current].forEach((o,idx)=>{html+=`<div class="option" onclick="selectMC(${idx})" data-idx="${idx}">${String.fromCharCode(65+idx)}. ${o.text}</div>`});
  } else if(q.type==='multi'){
    html+=`<p class="smallNote">Select all answers that apply.</p>`;
    shuffled[current].forEach((o,idx)=>{html+=`<div class="option" onclick="toggleMulti(${idx})" data-idx="${idx}">${String.fromCharCode(65+idx)}. ${o.text}</div>`});
  } else if(q.type==='blank'){
    html+=`<input class="blankInput" id="blankAnswer" type="text" placeholder="Type your answer here" autocomplete="off" />`;
  } else if(q.type==='drag'){
    html+=`<p class="smallNote">Drag each item into the correct box.</p><div class="dragArea" id="dragArea">`;
    shuffleArray(q.items.map((it,i)=>({it,i}))).forEach(obj=>{html+=`<div class="dragItem" draggable="true" ondragstart="drag(event)" id="drag-${obj.i}" data-orig="${obj.i}">${obj.it}</div>`});
    html+=`</div><div class="dropArea">`;
    q.zones.forEach((z,i)=>{html+=`<div class="dropZone" ondrop="drop(event)" ondragover="allowDrop(event)" data-zone="${i}"><strong>${z}</strong></div>`});
    html+=`</div>`;
  }
  html+=`<div class="feedback" id="feedback"></div>`;
  document.getElementById('questionBox').innerHTML=html;
  restoreResponse();
}
function selectMC(idx){if(locked[current])return;responses[current]=idx;document.querySelectorAll('.option').forEach(o=>o.classList.remove('selected'));document.querySelector(`[data-idx='${idx}']`).classList.add('selected');}
function toggleMulti(idx){if(locked[current])return;if(!Array.isArray(responses[current]))responses[current]=[];const pos=responses[current].indexOf(idx);if(pos>-1)responses[current].splice(pos,1);else responses[current].push(idx);document.querySelector(`[data-idx='${idx}']`).classList.toggle('selected');}
function allowDrop(ev){ev.preventDefault();}
function drag(ev){ev.dataTransfer.setData('text',ev.target.id);}
function drop(ev){ev.preventDefault();if(locked[current])return;const id=ev.dataTransfer.getData('text');const el=document.getElementById(id);const zone=ev.currentTarget;zone.appendChild(el);saveDrag();}
function saveDrag(){responses[current]=[...document.querySelectorAll('.dropZone')].map(z=>[...z.querySelectorAll('.dragItem')].map(i=>Number(i.dataset.orig))[0] ?? null);}
function restoreResponse(){
  const r=responses[current]; const q=questions[current];
  if(r===null)return;
  if(q.type==='mc')selectMC(r);
  if(q.type==='multi'&&Array.isArray(r)){r.forEach(i=>{const el=document.querySelector(`[data-idx='${i}']`);if(el)el.classList.add('selected');});}
  if(q.type==='blank'){document.getElementById('blankAnswer').value=r;}
  if(q.type==='drag'&&Array.isArray(r)){r.forEach((itemOrig,zoneIdx)=>{if(itemOrig!==null){const item=document.getElementById(`drag-${itemOrig}`);const zone=document.querySelector(`.dropZone[data-zone='${zoneIdx}']`); if(item&&zone)zone.appendChild(item);}})}
}
function checkAnswer(){
  const q=questions[current];
  if(q.type==='blank')responses[current]=document.getElementById('blankAnswer').value.trim().toLowerCase();
  if(q.type==='drag')saveDrag();
  const correct=isCorrect(current);
  locked[current]=true;
  const fb=document.getElementById('feedback');
  fb.className='feedback '+(correct?'correct':'incorrect');
  fb.textContent=correct?'Correct. Strong analysis.':'Submitted. Review the passage carefully before moving on.';
}
function isCorrect(i){
  const q=questions[i], r=responses[i];
  if(q.type==='mc'){return shuffled[i][r]?.orig===q.ans;}
  if(q.type==='multi'){
    if(!Array.isArray(r))return false;
    const chosen=r.map(idx=>shuffled[i][idx].orig).sort((a,b)=>a-b);
    const ans=[...q.ans].sort((a,b)=>a-b);
    return JSON.stringify(chosen)===JSON.stringify(ans);
  }
  if(q.type==='blank'){
    return q.ans.some(a=>String(r).toLowerCase().includes(a));
  }
  if(q.type==='drag'){
    return Array.isArray(r)&&JSON.stringify(r)===JSON.stringify(q.ans);
  }
}
function nextQuestion(){
  if(current < questions.length - 1){
    current++;
    renderQuestion();
    window.scrollTo({top:0, behavior:'smooth'});
  } else {
    showResults();
  }
}

function prevQuestion(){
  if(current > 0){
    current--;
    renderQuestion();
    window.scrollTo({top:0, behavior:'smooth'});
  }
}

function showResults(){
  let correct=0; questions.forEach((_,i)=>{if(isCorrect(i))correct++;});
  const pct=Math.round((correct/questions.length)*100);
  document.getElementById('progressFill').style.width='100%';
  let html=`<h1>Test Results</h1><p class="scoreBig">${pct}%</p><p><strong>${student}</strong>, you answered ${correct} out of ${questions.length} questions correctly.</p>`;
  if(pct>=70){
    html+=`<div class="certificate" id="certificate"><h1>Certificate of Achievement</h1><p>This certificate is proudly presented to</p><div class="certName">${student}</div><p>for successfully completing</p><h2>Ms. Clarke's English One Test</h2><p>with a score of</p><div class="scoreBig">${pct}%</div><p>Keep analyzing, citing evidence, and showing your brilliance.</p><p><strong>Teacher:</strong> Ms. Clarke</p></div><button onclick="window.print()">Print Certificate</button><button class="secondary" onclick="downloadCertificate()">Download Certificate</button>`;
  } else {
    html+=`<p class="smallNote">You did not reach 70% yet. Review theme, inference, structure, point of view, word meaning, and argument evidence before retesting.</p>`;
  }
  html+=`<h2>Standards Review</h2><table><tr><th>#</th><th>Standard</th><th>Result</th></tr>`;
  questions.forEach((q,i)=>{html+=`<tr><td>${i+1}</td><td>${q.std}</td><td>${isCorrect(i)?'Correct':'Review'}</td></tr>`});
  html+=`</table><button class="secondary" onclick="location.reload()">Restart Test</button>`;
  document.getElementById('resultsBox').innerHTML=html;
  showScreen('results');
}
function downloadCertificate(){
  const text=`Certificate of Achievement\n\nPresented to: ${student}\nFor successfully completing Ms. Clarke's English One Test.\nScore: ${Math.round((questions.filter((_,i)=>isCorrect(i)).length/questions.length)*100)}%\nTeacher: Ms. Clarke`;
  const blob=new Blob([text],{type:'text/plain'});
  const a=document.createElement('a');
  a.href=URL.createObjectURL(blob);
  a.download=`${student.replaceAll(' ','_')}_English_One_Certificate.txt`;
  a.click();
}
document.addEventListener('keydown',e=>{
  if((e.ctrlKey||e.metaKey)&&['c','v','x','a','s','p'].includes(e.key.toLowerCase())){e.preventDefault();}
});
</script>
</body>
</html>
