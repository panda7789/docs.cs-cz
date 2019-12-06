---
title: Volba přenosu
ms.date: 03/30/2017
helpviewer_keywords:
- choosing transports [WCF]
ms.assetid: b169462b-f7b6-4cf4-9fca-d306909ee8bf
ms.openlocfilehash: 69f2724182f83d507f749a150a8d006a4e0f2192
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74838062"
---
# <a name="choosing-a-transport"></a>Volba přenosu
Toto téma popisuje kritéria pro výběr ze tří hlavních přenosů, které jsou součástí Windows Communication Foundation (WCF): HTTP, TCP a pojmenované kanály. Služba WCF zahrnuje také přenos služby Řízení front zpráv (neboli MSMQ), ale tento dokument nepokrývá službu Řízení front zpráv.  
  
 Programovací model WCF odděluje operace koncového bodu (vyjádřené v kontraktu služby) od přenosového mechanismu, který spojuje dva koncové body. Získáte tak flexibilitu při rozhodování, jak vaše služby vystavovat v síti.  
  
 V rámci služby WCF určíte, jak přenést data mezi koncovými body pomocí *vazby*, která je tvořena sekvencí *prvků vazby*. Přenos je reprezentován prvkem transportní vazby, který je součástí vazby. Vazba obsahuje volitelné prvky vazby protokolu, jako je například zabezpečení, požadovaný element vazby kodéru zprávy a požadovaný prvek vazby přenosu. Přenos posílá nebo přijímá serializovanou formu zprávy do nebo z jiné aplikace.  
  
 Pokud se musíte připojit ke stávajícímu klientovi nebo serveru, možná nebudete moct používat konkrétní přenos. Služby WCF však lze zpřístupnit prostřednictvím více koncových bodů, z nichž každý má jiný přenos. Pokud jeden přenos nepokrývá zamýšlenou cílovou skupinu pro vaši službu, zvažte vystavení služby přes více koncových bodů. Klientské aplikace potom můžou použít koncový bod, který je pro ně nejvhodnější.  
  
 Po zvolení přenosu musíte vybrat vazbu, která ji používá. Můžete zvolit systémovou vazbu, která je [součástí systému,](../../../../docs/framework/wcf/system-provided-bindings.md)nebo můžete vytvořit vlastní vazbu (viz [vlastní vazby](../../../../docs/framework/wcf/extending/custom-bindings.md)). Můžete také vytvořit vlastní vazbu. Další informace najdete v tématu [vytváření uživatelsky definovaných vazeb](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md).  
  
## <a name="advantages-of-each-transport"></a>Výhody každého přenosu  
 Tato část popisuje hlavní důvody pro výběr jednoho ze tří hlavních přenosů, včetně podrobného rozhodovacího grafu pro výběr z nich.  
  
### <a name="when-to-use-http-transport"></a>Kdy použít přenos pomocí protokolu HTTP  
 HTTP je protokol požadavků a odpovědí mezi klienty a servery. Nejběžnější aplikace se skládá z klientů webového prohlížeče, kteří komunikují s webovým serverem. Klient odešle požadavek na server, který naslouchá zprávám požadavků klienta. Když server obdrží požadavek, vrátí odpověď, která obsahuje stav žádosti. V případě úspěchu se vrátí volitelná data, jako je například webová stránka, chybová zpráva nebo jiné informace. Další informace o protokolu HTTP najdete v tématu [http-Hypertext Transfer Protocol](https://go.microsoft.com/fwlink/?LinkId=94858).  
  
 Protokol HTTP není založen na připojení – po odeslání odpovědi se nezachová žádný stav. Aby bylo možné zpracovat transakce s více stránkami, aplikace musí zachovat potřebný stav.  
  
 V rámci WCF je vazba přenosu HTTP optimalizovaná pro interoperabilitu se staršími systémy než WCF. Pokud všechny komunikující strany používají WCF, jsou vazby na bázi TCP nebo pojmenované kanály rychlejší. Další informace naleznete v tématu <xref:System.ServiceModel.NetTcpBinding> a <xref:System.ServiceModel.NetNamedPipeBinding>.  
  
### <a name="when-to-use-the-tcp-transport"></a>Kdy použít přenos TCP  
 Protokol TCP je služba pro doručování s datovým proudem, která je založená na připojení s komplexní detekcí a opravou chyb. *Připojení* znamená, že před výměnou dat se navázala komunikační relace mezi hostiteli. Hostitel je jakékoli zařízení v síti TCP/IP identifikované logickou IP adresou.  
  
 TCP poskytuje spolehlivé doručování dat a snadné použití. Konkrétně protokol TCP upozorní odesílatele doručování paketů, zaručuje, že pakety budou doručeny ve stejném pořadí, ve kterém jsou odesílány, znovu přenáší ztracené pakety a zajistí, že datové pakety nebudou duplikovány. Upozorňujeme, že tato spolehlivé doručování se používá mezi dvěma uzly TCP/IP a není totéž jako *WS-ReliableMessaging*, která platí pro koncové body, bez ohledu na to, kolik zprostředkujících uzlů můžou zahrnovat.  
  
 Přenos WCF TCP je optimalizován pro scénář, kde obě konce komunikace používají WCF. Tato vazba je nejrychlejší vazbou WCF pro scénáře, které zahrnují komunikaci mezi různými počítači. Výměna zpráv používá <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> pro optimalizaci přenosu zpráv. Protokol TCP poskytuje duplexovou komunikaci, takže ji můžete použít k implementaci duplexních smluv, a to i v případě, že je klient za překladem adres (NAT).  
  
### <a name="when-to-use-the-named-pipe-transport"></a>Kdy použít přenos pojmenovaného kanálu  
 Pojmenovaný kanál je objekt v jádru operačního systému Windows, například část sdílené paměti, kterou procesy můžou použít ke komunikaci. Pojmenovaný kanál má název a lze ho použít pro jednosměrnou nebo duplexnou komunikaci mezi procesy na jednom počítači.  
  
 Pokud je komunikace mezi různými aplikacemi WCF v jednom počítači vyžadována a chcete zabránit jakékoli komunikaci z jiného počítače, použijte přenos pojmenovaných kanálů. Dalším omezením je, že procesy běžící z vzdálené plochy systému Windows mohou být omezeny na stejnou relaci vzdálené plochy systému Windows, pokud nemají zvýšená oprávnění.  
  
> [!WARNING]
> Při použití přenosu pojmenovaného kanálu se slabým zástupným znakem adresy URL ve více lokalitách hostovaných ve službě IIS může dojít k následující chybě: v aktivační službě ' NetPipeActivator ' protokolu ' NET. pipe ' došlo k chybě při pokusu o naslouchání webu ' 2 '. Proto je protokol pro web dočasně zakázán. Další podrobnosti najdete ve zprávě výjimky. Adresa URL: WeakWildcard: NET. pipe:/\<název počítače >/status: ConflictingRegistration výjimka: název procesu: ID procesu SMSvcHost: 1076 \  
  
## <a name="decision-points-for-choosing-a-transport"></a>Rozhodovací body pro výběr přenosu  
 V následující tabulce jsou popsány běžné rozhodovací body používané k výběru přenosu. Měli byste uvažovat o všech dalších atributech a přenosech, které se vztahují k vaší aplikaci. Identifikujte atributy, které jsou pro vaši aplikaci důležité, identifikujte přenosy, které přidružuje favorably k jednotlivým atributům, a pak vyberte přenosy, které nejlépe fungují s nastaveným atributem.  
  
|Atribut|Popis|Upřednostněné přenosy|  
|---------------|-----------------|------------------------|  
|Diagnostika|Diagnostika umožňuje automaticky detekovat problémy s připojením k přenosu. Všechny přenosy podporují možnost odesílat informace o chybě, které popisují připojení. Technologie WCF však neobsahuje diagnostické nástroje pro zkoumání problémů se sítí.|Žádné|  
|Hosting|Všechny koncové body WCF musí být hostovány v rámci aplikace. Služba IIS 6,0 a starší verze podporují pouze hostování aplikací, které používají přenos pomocí protokolu HTTP. V systému Windows Vista je přidána podpora pro hostování všech přenosů WCF, včetně TCP a pojmenovaných kanálů. Další informace najdete v tématu [hostování v Internetová informační služba](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md) a [hostování v aktivační službě procesů systému Windows](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md).|HTTP|  
|Určených|Kontrola je schopnost extrahovat a zpracovávat informace ze zpráv během přenosu. Protokol HTTP odděluje informace o směrování a řízení z dat, což usnadňuje vytváření nástrojů, které kontrolují a analyzují zprávy. Přenosy, které se dají snadno kontrolovat, můžou také vyžadovat menší výpočetní výkon u síťových zařízení. Úroveň zabezpečení má vliv na to, zda lze kontrolovat zprávy.|HTTP|  
|Čekací doba|Latence je minimální doba potřebná k dokončení výměny zpráv. Všechny síťové operace mají více nebo méně latencí v závislosti na výběru přenosů. Použití duplexní nebo jednosměrné komunikace s přenosem, jehož nativní výměna zpráv je požadavek-odpověď, například HTTP, může způsobit další latenci z důvodu vynucené korelace zpráv. V takové situaci zvažte použití přenosu, jehož nativní výměna zpráv je duplexní, jako je například TCP.|TCP s názvem<br /><br /> Příkazem|  
|Reach|Dosah přenosu vyjadřuje, jak se podporuje přenos v připojení k ostatním systémům. Přenos pojmenovaného kanálu má velmi malý přístup; může se připojit jenom ke službám běžícím na stejném počítači. Přenosy TCP a HTTP mají vynikající dosah a můžou proniknout některé konfigurace NAT a brány firewall. Další informace najdete v tématu [práce s NAT a branami firewall](../../../../docs/framework/wcf/feature-details/working-with-nats-and-firewalls.md).|HTTP, TCP|  
|Zabezpečení –|Zabezpečení je schopnost chránit zprávy během přenosu prostřednictvím poskytnutí důvěrnosti, integrity nebo ověřování. Důvěrnost chrání před tím, než se zpráva ověřuje, integrita chrání zprávu před jejich úpravou a ověřování poskytuje informace o odesílateli nebo příjemci zprávy.<br /><br /> WCF podporuje zabezpečení přenosu jak na úrovni zprávy, tak na úrovni přenosu. Pokud přenos podporuje režim přenosu s vyrovnávací pamětí, zavede se zabezpečení zpráv do přenosu. Podpora zabezpečení přenosu se liší v závislosti na zvoleném přenosu. Přenosy HTTP, TCP a Named pipe mají v rámci podpory zabezpečení přenosu rozumnou paritu.|Vše|  
|Propustnost|Propustnost měří množství dat, která je možné přenést a zpracovat v zadaném časovém období. Podobně jako latence může zvolený přenos ovlivnit propustnost operací služby. Maximalizace propustnosti přenosu vyžaduje minimalizaci režie na přenos obsahu a minimalizaci času stráveného čekáním na vyplňování zpráv. Přenos TCP i pojmenovaného kanálu zvyšuje režijní náklady na tělo zprávy a podporují nativní duplexní tvar, který zkracuje čekání na odpověď na zprávu.|TCP, pojmenovaný kanál|  
|Nástroje|Nástroje představují podporu aplikací třetích stran pro protokol pro vývoj, diagnostiku, hostování a další činnosti. Vývoj nástrojů a softwaru pro práci s protokolem HTTP znamená obzvláště velkou investici.|HTTP|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.WSHttpBinding>
- <xref:System.ServiceModel.WSDualHttpBinding>
- <xref:System.ServiceModel.WSFederationHttpBinding>
- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
- <xref:System.ServiceModel.NetTcpBinding>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
- <xref:System.ServiceModel.NetNamedPipeBinding>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>
- [Vazby](../../../../docs/framework/wcf/feature-details/bindings.md)
- [Vazby poskytované systémem](../../../../docs/framework/wcf/system-provided-bindings.md)
- [Vytváření uživatelem definovaných vazeb](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)
