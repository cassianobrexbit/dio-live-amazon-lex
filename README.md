# dio-live-amazon-lex
Repositório para o Live Coding do dia 28/10/2021

## Serviços utilizados

- Amazon Lex

## Etapas para o desenvolvimento

### Criando o chatbot

- Acessar o Console do Amazon Lex
- Create bot
- Creation methd [Create] -> Bot name [nome_do_bot] -> IAM permissions [Create role with basic Amazon Lex permissions] -> COPPA [No] -> Idle session timeout [padrão 5m] -> Next
- Language [English US] -> Restante das configurações padrão -> Done

### Configurando um intent

- Intent details -> Intent name [SearchCourse] -> Description optional
- Utterances [hi, hey, hello, hello DIOBot, hi DIOBot] -> Add Utterance
- Confirmation prompts and decline responses [Active]
- Closing Responses [Active]
- Save intent

### Criando tipos de slots para um intent

- Intents list -> Selecionar o intent criado

- Slot types -> Add blank slot type -> Slot type name [InterestArea]
- Slot value resolution [Restric to slot values]
- Slot type values [Artificial Intelligence: [AI, Machine learning, Artificial Intelligence, Deep Learning], Web Development: [API, Serverless, Lambda, JavaScript, AWS, NodeJS, Python], [Frontend Development: [Web Design, ReactJS, AngularJS, VueJS]] -> Add Value
- Save slot type

- Slot types -> Add blank slot type -> Slot type name [ClassType]
- Slot value resolution [Restric to slot values]
- Slot type values [Live Coding: [lives, live coding, live], [Courses: [courses, courses] [Labs: [lab, labs, laboratories, laboratory]] -> Add Value
- Save slot type

### Adicionando slots a um intent

- Intents list -> selecionar o intent criado -> Slots -> Add slot

- Name [Name] -> Slot type [AMAZON.FirstName] -> Prompts [Hello Dev! My name is DIOBot To start our trip, tell me your name please :)] -> Add
- Add Slot

- Name [InterestArea] -> Slot type [InterestArea] -> Prompts [Welcome {Name}! I will help you to find courses based on your interests. Please tell me your preferred area :) You can choose one of these options: Artificial Intelligence, Web Development and Frontend Development.] -> Add


- Add Slot
- Name [ClassType] -> Slot type [ClassType] -> Prompts [Amazing! {InterestArea} is an excellent choice. Now we need to know what type of classes you prefer. So chose one of three options as follow: Course, Live Coding or Labs] -> Add

- Add Slot
- Name [ClassTime] -> Slot type [AMAZON.Time] -> Prompts [Perfect {Name}! We're almost done. Now, select one of below options of date to start your {ClassType} of {InterestArea}.] -> Add
  - Advanced options -> Slot prompts -> Bot elicits information -> More prompt options -> Add -> Add card group -> Card 1 -> Title [Chose your preferred time] -> Buttons -> Add Button [09:00 - 9 AM] (repetir o passo com outros horários)
  - 
- Add Slot
- Name [nome] -> Slot type [AMAZON.EmailAddress] -> Prompts [Nice! The last thing we need is your email. We'll send some additional informations to you.] -> Add

- Confirmation prompts and decline responses

  - Confirmation prompts [Right! Now we are done. Your schedule is {ClassType} of {InterestArea} scheduled to {ScheduleDate} Please say "Yes" to confirm or "No" to decline.]
  - Decline responses [Ok, see you next time. I'll miss you until you came here again. Please don't forget me. I love you.]

- Fulfillment

  - On successful fulfillment [Nice! That's perfect. Your schedule was confirmed.]
  - In case of failure [That's bad. SOmething went wrong =(.]
  
- Closing responses
  - Response sent to the user after the intent is fulfilled [That's all done.]

- Save intent
- Build
- Test

