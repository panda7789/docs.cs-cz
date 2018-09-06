---
title: Volba přenosu
ms.date: 03/30/2017
helpviewer_keywords:
- choosing transports [WCF]
ms.assetid: b169462b-f7b6-4cf4-9fca-d306909ee8bf
ms.openlocfilehash: c98fd4bb76074c2d96b702a37bf1964600d365e3
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43864625"
---
# <a name="choosing-a-transport"></a>Volba přenosu
Toto téma popisuje kritéria pro výběr mezi tři hlavní přenosy, které jsou zahrnuté ve Windows Communication Foundation (WCF): HTTP, TCP a pojmenované kanály. Zahrnuje také WCF přenosu služby Řízení front zpráv (MSMQ), ale tento dokument nepopisuje služby Řízení front zpráv.  
  
 Programovacího modelu WCF odděluje operace koncového bodu (jak je vyjádřen v kontraktu služby), od přenos mechanismus, který se připojuje dva koncové body. Získáte flexibilitu při rozhodování, jak vystavit svoje služby na síti.  
  
 Ve službě WCF, můžete určit, jak přenášet data přes síť mezi koncové body pomocí *vazby*, který se skládá z posloupnosti *elementů vazby*. Přenos je reprezentován element vazby přenosu, která je součástí vazby. Vazby zahrnuje volitelné protokol elementy vazby, jako je zabezpečení, element vazby kodér požadovaná zpráva a element vazby přenosu vyžaduje. Přenos odesílá nebo přijímá serializovanou formu zprávu do nebo z jiné aplikace.  
  
 Pokud se musí připojit k existující klient nebo server, nemusí mít možnost použití konkrétní přenos. Ale WCF služby můžou být přístupné přes několik koncových bodů, každý s jiný přenos. Pokud jeden přenos nepopisuje jeho zamýšlenou cílovou skupinou pro vaši službu, vezměte v úvahu vystavení služby přes několik koncových bodů. Klientské aplikace pak můžete použít koncový bod, který je pro ně nejvhodnější.  
  
 Až zvolíte, přenos, je nutné vybrat vazbu, která ji používá. Můžete také vazeb poskytovaných systémem (naleznete v tématu [System-Provided vazby](../../../../docs/framework/wcf/system-provided-bindings.md)), nebo můžete vytvořit vlastní vlastní vazby (naleznete v tématu [vlastních vazeb](../../../../docs/framework/wcf/extending/custom-bindings.md)). Můžete také vytvořit vlastní vazby. Další informace najdete v tématu [Creating User-Defined vazby](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md).  
  
## <a name="advantages-of-each-transport"></a>Výhody každé přenosu  
 Tato část popisuje hlavní důvody pro klepnutím na některou ze tří hlavních přenosů, včetně podrobných rozhodovací graf pro výběr mezi nimi.  
  
### <a name="when-to-use-http-transport"></a>Kdy použít přenos pomocí protokolu HTTP  
 HTTP je požadavek/odpověď protokolu mezi klienty a servery. Nejčastěji používané aplikace se skládá z webových klientů, které komunikují s webovým serverem. Klient odešle požadavek na server, který přijímá zprávy požadavku klienta. Pokud server přijme požadavek, vrátí odpověď, která obsahuje stav žádosti o. Pokud je úspěšná, je vrácena volitelnými daty, jako jsou webové stránky, chybová zpráva nebo jiné informace. Další informace o protokolu HTTP, naleznete v tématu [HTTP - Hypertext Transfer Protocol](https://go.microsoft.com/fwlink/?LinkId=94858).  
  
 Protokol HTTP není založena na připojení, jakmile je odeslána odpověď, žádný stav není zachován. Zpracování transakcí více stránek, aplikace musí zachovat všechny nezbytné stavu.  
  
 Ve službě WCF, přenos pomocí protokolu HTTP vazby je optimalizován pro spolupráci s systémy starší než – WCF. Pokud všechny komunikujících stran používají WCF, jsou založené na TCP nebo pojmenované kanály na základě vazby rychlejší. Další informace naleznete v tématu <xref:System.ServiceModel.NetTcpBinding> a <xref:System.ServiceModel.NetNamedPipeBinding>.  
  
### <a name="when-to-use-the-tcp-transport"></a>Kdy použít přenosu protokolu TCP  
 TCP je služba pro přenos na základě připojení, orientovaný na stream s začátku do konce Chyba zjišťování a opravy. *Na základě připojení* znamená, že je před výměna dat vytvoří relaci komunikaci mezi hostiteli. Hostitele je žádné zařízení v síti TCP/IP identifikovaný podle logického IP adresy.  
  
 TCP poskytuje přenos dat spolehlivé a snadné použití. Konkrétně TCP upozorní odesílatele doručování paketů zaručuje, že pakety budou doručeny ve stejném pořadí, v níž jsou odesílány, odešle ke ztrátě paketů a zajistí, že se neduplikují datových paketů. Mějte na paměti, že toto spolehlivé doručování mezi dvěma uzly TCP/IP se vztahuje a není totéž jako *WS-ReliableMessaging*, které platí mezi koncovými body, bez ohledu na to, kolik zprostředkující uzly mohou zahrnovat.  
  
 Přenos WCF TCP je optimalizovaný pro scénář, ve kterém jsou obě strany komunikace pomocí technologie WCF. Tato vazba je nejrychlejší vazby WCF pro scénáře, které zahrnují komunikaci mezi různé počítače. Zpráva vymění použití <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> pro přenos zpráv optimalizované. TCP poskytuje duplexní komunikaci a proto lze použít k implementaci duplexní kontrakty, i když je klient za překlad síťových adres (NAT).  
  
### <a name="when-to-use-the-named-pipe-transport"></a>Kdy použít pojmenovaný kanál přenosu  
 Pojmenovaný kanál je objekt v jádru operačního systému Windows, jako je například část sdílené paměti, procesy, které můžete použít pro komunikaci. Pojmenovaný kanál s názvem a je možné pro jednosměrné nebo obousměrné komunikace mezi procesy na jednom počítači.  
  
 Při komunikaci se vyžaduje mezi různými aplikacemi WCF v jednom počítači a chcete zabránit libovolné komunikaci z jiného počítače, potom pomocí pojmenovaných kanálů přenosu. Další omezení je, že procesy spouštěné z vzdálené plochy Windows může být omezena na stejné relace vzdálené plochy Windows, pokud jste se zvýšenými oprávněními.  
  
> [!WARNING]
>  Pokud používáte pojmenovaný kanál přenosu slabé zástupné rezervaci adresy URL na více weby hostované ve službě IIS, může dojít k následující chybě: došlo k chybě v aktivační službě "NetPipeActivator" protokolu "net.pipe" při pokusu o naslouchání serveru '2' proto protokolu je zakázaná pro web dočasně. Zobrazit zpráva o výjimce pro další podrobnosti. Adresa URL: WeakWildcard:net.pipe:/\<název počítače > / Stav: výjimka ConflictingRegistration: název procesu: SMSvcHost ID procesu: 1076\  
  
## <a name="decision-points-for-choosing-a-transport"></a>Rozhodovací body pro volba přenosu  
 Následující tabulka popisuje běžné rozhodovací body používané k výběru přenos. Měli byste zvážit všechny další atributy a přenosy, které se vztahují k vaší aplikaci. Určení atributů, které jsou důležité pro vaši aplikaci, identifikovat přenosy, které spojují příznivě s jednotlivými svoje atributy a vyberte přenosy, které fungují nejlépe s sady atributů.  
  
|Atribut|Popis|Dána přenosy|  
|---------------|-----------------|------------------------|  
|Diagnostika|Diagnostika umožňují automaticky detekovat potíže s připojením k přenosu. Všechny přenosy podporují schopnost posílání informací zpět selhání, který popisuje připojení. WCF nezahrnuje diagnostické nástroje pro zkoumání problémů se sítí.|Žádné|  
|Hostování|Všechny koncové body WCF musí být hostovaný uvnitř aplikace. [!INCLUDE[iis601](../../../../includes/iis601-md.md)] a starší podporují pouze hostitelské aplikace, které používají přenos pomocí protokolu HTTP. Na [!INCLUDE[wv](../../../../includes/wv-md.md)], podpora bude přidána pro hostování všechny přenosy WCF, včetně TCP a pojmenované kanály. Další informace najdete v tématu [hostování v Internetové informační službě](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md) a [hostování v aktivační službě procesů Windows](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md).|HTTP|  
|Kontrola|Kontrola je schopnost extrahování a zpracování informací od zpráv během přenosu. Protokol HTTP odděluje směrování a ovládací prvek informace z dat, což usnadňuje vytváření buildů, které kontrolovat a analyzovat zprávy. Přenosy, které se dají snadno ke kontrole, budete možná muset méně výpočetní výkon v síťových zařízení. Úroveň zabezpečení používá dopady, zda zprávy můžete prozkoumat.|HTTP|  
|Latence|Latence je minimální množství dobu potřebnou k provedení výměny zpráv. Všechny síťové operace mají vyšší nebo nižší latenci v závislosti na výběru přenosu. Duplexní nebo jednosměrnou komunikaci pomocí přenosu, jehož vzoru výměny zpráv nativní je požadavek odpověď, jako je například HTTP, může způsobit další latence kvůli vynucené korelace zprávy. V takovém případě zvažte použití přenosu, jehož vzoru výměny zpráv nativní je duplexní, jako je například TCP.|TCP, s názvem<br /><br /> Kanál|  
|Dosah|Dosah přenos odráží, jak podporující přenos je na propojení s jinými systémy. Pojmenovaný kanál přenosu má velmi malé dosah; můžete připojit jenom na služby spuštěné na stejném počítači. Přenosy TCP nebo HTTP mají vynikající dosah a umožňuje pronikat branami některé konfigurace překladu adres a brány firewall. Další informace najdete v tématu [práce s NAT a brány firewall](../../../../docs/framework/wcf/feature-details/working-with-nats-and-firewalls.md).|HTTP, TCP|  
|Zabezpečení|Zabezpečení je schopnost zadáním důvěrnost, integritu nebo ověřování ochrana zprávy během přenosu. Důvěrnost zkoumají chrání zprávu, chrání integritu zprávu nebylo možné měnit a ověřování poskytuje záruky týkající se odesílatel nebo příjemce zprávy.<br /><br /> WCF podporuje zabezpečení přenosu i na úrovni zpráv a úrovni přenosu. Zabezpečení zpráv lze kombinovat s přenosu, zda přenos podporuje režim přenosu ve vyrovnávací paměti. Podpora pro zabezpečení přenosu se liší v závislosti na zvolené přenosu. HTTP, TCP a přenosy pojmenovaného kanálu mají přiměřené parity v podpoře pro zabezpečení přenosu.|Všechny|  
|Propustnost|Propustnost se měří množství dat, která můžou přenášet a zpracovány v zadaném časovém období. Třeba latence mohou ovlivnit zvolené přenosu propustnosti pro operace služby. Maximální využití propustnosti pro přenos vyžaduje, minimalizovat nároky odesílání obsahu, stejně jako minimalizovat čas strávený čekání na dokončení výměny zpráv. TCP i přenosy pojmenovaného kanálu přidat nízkou režií text zprávy a podporují nativní duplexní obrazce, která organizacím snižuje čekat na zprávy odpovědi.|TCP, pojmenovaného kanálu|  
|Nástroje|Nástroje představuje podporu pro protokol pro vývoj, diagnostiky, hostování a dalších aktivit aplikaci třetí strany. Vývoj nástroje a software pro práci s protokolem HTTP označuje, že zejména velkých investic.|HTTP|  
  
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
