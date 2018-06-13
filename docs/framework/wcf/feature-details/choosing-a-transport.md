---
title: Volba přenosu
ms.date: 03/30/2017
helpviewer_keywords:
- choosing transports [WCF]
ms.assetid: b169462b-f7b6-4cf4-9fca-d306909ee8bf
ms.openlocfilehash: 7f1b356bdb70c9a7fd94f45c5c4424eebe822049
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33495532"
---
# <a name="choosing-a-transport"></a>Volba přenosu
Toto téma popisuje kritéria pro výběr mezi tři hlavní přenosy, které jsou zahrnuté ve Windows Communication Foundation (WCF): HTTP, TCP a pojmenované kanály. Také zahrnuje WCF řízení front zpráv (MSMQ) přenosu, ale tento dokument nepopisuje služby Řízení front zpráv.  
  
 Programovací model WCF odděluje operace koncového bodu (jak je vyjádřen v kontraktu služby), od přenosový mechanismus, který se připojuje dva koncové body. To vám dává možnost rozhodnout, jak vystavit vaší služby k síti.  
  
 Ve službě WCF, můžete určit, jak k přenosu dat v síti mezi koncovými body pomocí *vazby*, který se skládá z posloupnost *elementů vazby*. Přenos je reprezentována element vazby přenosu, která je součástí vazby. Vazba zahrnuje elementů vazby volitelné protokolu, například zabezpečení, element požadované zpráva kodér vazby a element vazby požadované přenosu. Přenos odešle nebo přijme serializovaný formu zprávu do nebo z jiné aplikace.  
  
 Pokud se musí připojit do existujícího klienta nebo serveru, nemusí mít volba o použití konkrétního přenosu. Ale služby WCF můžete být přístupné přes několik koncových bodů, každý s různé přenosové. Pokud jeden přenos nepokrývá předpokládanou cílovou skupinou pro vaši službu, zvažte, vystavení službu přes několik koncových bodů. Klientské aplikace pak může použít k koncového bodu, který je nejvhodnější pro ně.  
  
 Po kliknutí na přenos, je nutné vybrat vazbu, která jej používá. Můžete zvolit vazby poskytované systémem (najdete v části [System-Provided vazby](../../../../docs/framework/wcf/system-provided-bindings.md)), nebo můžete vytvořit vlastní vlastní vazby (najdete v části [vlastní vazby](../../../../docs/framework/wcf/extending/custom-bindings.md)). Můžete také vytvořit vlastní vazby. Další informace najdete v tématu [Creating User-Defined vazby](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md).  
  
## <a name="advantages-of-each-transport"></a>Výhody každý přenosu  
 Tato část popisuje hlavních důvodů pro výběr některého tři hlavní přenosy, včetně podrobné rozhodovací graf pro výběr mezi nimi.  
  
### <a name="when-to-use-http-transport"></a>Kdy použít přenos HTTP  
 HTTP je požadavek a odpověď protokolu mezi klienty a servery. Nejběžnější aplikace se skládá z webového prohlížeče klienty, kteří komunikují webového serveru. Klient odešle požadavek na server, které přijímají zprávy požadavku klienta. Když server přijme požadavek, vrátí odpověď, která obsahuje stav žádosti. Pokud úspěšné, vrátí se volitelná data, například na webové stránce, chybovou zprávu nebo Další informace. Další informace o protokolu HTTP, najdete v části [HTTP - Hypertext Transfer Protocol](http://go.microsoft.com/fwlink/?LinkId=94858).  
  
 Protokol HTTP není založeného na připojení – po odeslání odpovědi je žádný stav není zachován. Pro zpracování transakcí několika page, aplikace musí zachovat všechny nezbytné stavu.  
  
 Ve službě WCF, přenos HTTP vazba je optimalizovaná pro spolupráci s systémy starší než WCF. Pokud všechny komunikující strany používají WCF, je založená na TCP nebo pojmenované kanály na základě vazby rychlejší. Další informace naleznete v tématu <xref:System.ServiceModel.NetTcpBinding> a <xref:System.ServiceModel.NetNamedPipeBinding>.  
  
### <a name="when-to-use-the-tcp-transport"></a>Kdy použít přenos TCP  
 TCP je služba doručení založeného na připojení, orientovaný datový proud s rozpoznávání a opravy chyb začátku do konce. *Na základě připojení* znamená, že je před zahájením výměny dat navázat relaci komunikace mezi hostiteli. Hostitel je jakékoli zařízení v síti TCP/IP identifikovaný logické IP adresu.  
  
 TCP poskytuje přenos dat spolehlivé a snadné použití. Konkrétně TCP upozorní odesílatel doručování paketů zaručuje, že pakety jsou dodávány ve stejném pořadí, v níž jsou odesílány, odešle ke ztrátě paketů a zajišťuje, že se neduplikují datových paketů. Upozorňujeme, že tento spolehlivé doručení platí mezi dvěma uzly TCP/IP a není totéž jako *WS-ReliableMessaging*, které se vztahují mezi koncovými body, bez ohledu na to, kolik zprostředkující uzlů může zahrnovat.  
  
 Přenos WCF TCP je optimalizovaný pro scénář, kde se oba konce komunikaci pomocí WCF. Tato vazba je nejrychlejší vazby WCF pro scénáře, které zahrnují komunikaci mezi různé počítače. Zpráva výměny použití <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> pro přenos zpráv optimalizované. TCP poskytuje duplexní komunikace a tak lze použít k implementaci duplexní kontrakty, i když je klient za překlad síťových adres (NAT).  
  
### <a name="when-to-use-the-named-pipe-transport"></a>Kdy použít přenos pojmenovaný kanál  
 Pojmenovaný kanál je objekt jádra systému Windows, operačního systému, jako je oddíl sdílené paměti, které procesy můžete použít pro komunikaci. Pojmenovaný kanál, má název a lze použít pro jednosměrné nebo obousměrné komunikace mezi procesy na jednom počítači.  
  
 Při komunikaci se vyžaduje mezi různými aplikacemi WCF v jednom počítači a chcete zabránit žádné komunikace z jiného počítače, pak používají pojmenované kanály přenos. Další omezení je, procesů spuštěných ze vzdálené plochy Windows můžou být omezené na stejné relace vzdálené plochy Windows, pokud se zvýšenými oprávněními.  
  
> [!WARNING]
>  Při použití pojmenovaného kanálu přenosu s rezervaci adresy URL slabé zástupný znak v několika lokalitách hostovaný ve službě IIS, může dojít k následující chybě: došlo k chybě ve službě Aktivace 'NetPipeActivator' protokolu 'net.pipe' při pokusu o naslouchat webu: 2. proto tento protokol je pro lokalitu dočasně zakázána. Zobrazí se zpráva výjimky další podrobnosti. Adresa URL: WeakWildcard:net.pipe:/\<název počítače > / Stav: výjimka ConflictingRegistration: název procesu: SMSvcHost ID procesu: 1076\  
  
## <a name="decision-points-for-choosing-a-transport"></a>Rozhodovací body pro volba přenosu  
 Následující tabulka popisuje běžné rozhodovací body používané zvolit přenos. Měli byste zvážit všechny další atributy a přenosy, které se vztahují k vaší aplikaci. Identifikovat atributy, které jsou důležité pro vaši aplikaci, identifikovat přenosy, které příznivě přidružit k jednotlivým vaší atributů a potom vyberte přenosy, které fungují s atributem nastaveným.  
  
|Atribut|Popis|Podporuje přenosy|  
|---------------|-----------------|------------------------|  
|Diagnostika|Diagnostika umožňují automaticky zjišťovat potíže s připojením k přenosu. Všechny přenosy podporují schopnost posílání informací back selhání, který popisuje připojení. WCF však nezahrnuje diagnostické nástroje pro zkoumání problémů se sítí.|Žádné|  
|Hostování|Všechny koncové body WCF musí být hostované uvnitř aplikace. [!INCLUDE[iis601](../../../../includes/iis601-md.md)] a starší podpora pouze hostování aplikací, které používají přenos HTTP. Na [!INCLUDE[wv](../../../../includes/wv-md.md)], bude přidána pro hostování všechny přenosy WCF, včetně TCP a pojmenované kanály podpory. Další informace najdete v tématu [hostování v Internetové informační službě](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md) a [hostování v aktivační službě procesů systému Windows](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md).|HTTP|  
|Kontroly|Kontroly je možnost extrahovat a zpracování informací z zprávy během přenosu. Protokol HTTP odděluje směrování a řízení informace z dat, což usnadňuje sestavení nástroje, které kontrolují a analyzovat zprávy. Přenosy, které se snadno zkontrolovat může také vyžadovat méně výpočetní výkon v síťových zařízení. Úroveň zabezpečení používá ovlivňuje, jestli může být prověřovány zprávy.|HTTP|  
|Čekací doba|Latence je minimální množství času potřebné pro dokončení výměny zpráv. Všechny síťové operace mají vyšší nebo nižší latenci v závislosti na volba přenosu. Duplexní nebo jednosměrnou komunikaci pomocí přenosu, jejichž vzorce výměny zpráv nativní je, že požadavek odpověď, jako je například HTTP, může způsobit další latence kvůli vynucené korelace zpráv. V této situaci zvažte použití přenosu, jejichž vzorce výměny zpráv nativní je duplexní, jako je například protokol TCP.|TCP, s názvem<br /><br /> kanálu|  
|Reach|Rozsah přenos odráží, jak podporující přenosu je v připojení s jinými systémy. Pojmenovaný kanál přenosu má velmi malé reach; lze připojit pouze k služby spuštěné na stejném počítači. Přenosy TCP a HTTP mít vynikající reach a můžete proniknout některé konfigurace NAT a brány firewall. Další informace najdete v tématu [práce se zařízeními NAT a brány firewall](../../../../docs/framework/wcf/feature-details/working-with-nats-and-firewalls.md).|PROTOKOLU HTTP, TCP|  
|Zabezpečení|Zabezpečení je možnost chránit zprávy při přenosu zadáním důvěrnost, integritu a ověřování. Důvěrnost chrání zprávu z se zkontrolován, integritu chrání zprávu nebylo možné měnit a ověřování umožňuje záruky o odesílatele a příjemce zprávy.<br /><br /> WCF podporuje zabezpečení přenosu jak na úrovni zpráv a na úrovni přenosu. Zabezpečení zpráv vytvoří se přenos, zda přenos podporuje režim přenosu ve vyrovnávací paměti. Podpora pro zabezpečení přenosu se liší v závislosti na zvolené přenosu. HTTP, TCP a přenosy pojmenovaný kanál mít přiměřené paritní v podpoře pro zabezpečení přenosu.|Všechny|  
|Propustnost|Propustnost měří množství dat, které mohou být odeslány a zpracovány v zadaném časovém období. Latence, jako je zvolený přenos může ovlivnit propustnost pro operace služby. Maximální využití propustnost pro přenos vyžaduje minimalizaci režie přenosu obsahu a také minimalizovat čas strávený čekání na dokončení výměny zpráv. TCP i přenosy pojmenovaný kanál přidejte malé nároky na text zprávy a podporují nativní duplexní tvar, který snižuje čekání odpovědí na zprávy.|TCP, pojmenovaný kanál|  
|Nástrojů|Nástrojů představuje podporu aplikace třetích stran pro protokol pro vývoj, diagnostiku, hostování a dalšími aktivitami. Vývoj nástrojů a softwaru pro práci s protokolem HTTP označuje zvlášť velké investice.|HTTP|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`>  
  <<!--zz <xref:System.ServiceModel.WsDualHttpBinding> --> `System.ServiceModel.WsDualHttpBinding`
 <<!--zz <xref:System.ServiceModel.WsFederationHttpBinding>  --> `System.ServiceModel.WsFederationHttpBinding` <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
 <xref:System.ServiceModel.NetTcpBinding>  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
 <xref:System.ServiceModel.NetNamedPipeBinding>  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
 [Vazby](../../../../docs/framework/wcf/feature-details/bindings.md)  
 [Vazby poskytované systémem](../../../../docs/framework/wcf/system-provided-bindings.md)  
 [Vytváření uživatelem definovaných vazeb](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)
