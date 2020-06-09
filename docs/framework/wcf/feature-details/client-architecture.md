---
title: Architektura klienta
ms.date: 03/30/2017
ms.assetid: 02624403-0d77-41cb-9a86-ab55e98c7966
ms.openlocfilehash: c873368b82551312d203eb28d208eb6e3f50c89b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84586998"
---
# <a name="client-architecture"></a>Architektura klienta
Aplikace používají klientské objekty služby Windows Communication Foundation (WCF) k vyvolání operací služby. Toto téma popisuje objekty klienta WCF, kanály klientů WCF a jejich vztahy k základní architektuře kanálu. Základní přehled objektů klienta WCF najdete v tématu [Přehled klientů WCF](../wcf-client-overview.md). Další informace o vrstvě kanálu najdete v tématu [rozšíření vrstvy kanálu](../extending/extending-the-channel-layer.md).  
  
## <a name="overview"></a>Přehled  
 Doba běhu modelu služby vytvoří klienty WCF, které se skládají z následujících:  
  
- Automaticky generovaná implementace klienta kontraktu služby, která zapíná volání z kódu aplikace do odchozích zpráv a zapíná odpovědi na výstupní parametry a vrací hodnoty, které může vaše aplikace načíst.  
  
- Implementace rozhraní ovládacího prvku ( <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> ), která seskupuje různá rozhraní a poskytuje přístup k funkcím řízení, zejména schopnost ukončit relaci klienta a odstranit kanál.  
  
- Kanál klienta, který je sestaven na základě nastavení konfigurace určeného použitou vazbou.  
  
 Aplikace mohou vytvořit takové klienty na vyžádání, a to buď prostřednictvím, <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> nebo vytvořením instance <xref:System.ServiceModel.ClientBase%601> odvozené třídy, která je generována nástrojem pro nástroj pro tvorbu [metadat (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md). Tyto připravené třídy klienta zapouzdřují a přenesly do implementace klientského kanálu, který je dynamicky vytvořen pomocí <xref:System.ServiceModel.ChannelFactory> . Proto kanál klienta a objekt pro vytváření kanálů, který je vytváří, jsou kontaktním bodem zájmu této diskuze.  
  
## <a name="client-objects-and-client-channels"></a>Klientské objekty a klientské kanály  
 Základní rozhraní klientů WCF je <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> rozhraní, které zpřístupňuje základní funkce klienta a také základní funkce objektu komunikace <xref:System.ServiceModel.ICommunicationObject?displayProperty=nameWithType> , funkce kontextu <xref:System.ServiceModel.IContextChannel?displayProperty=nameWithType> a rozšiřitelné chování nástroje <xref:System.ServiceModel.IExtensibleObject%601?displayProperty=nameWithType> .  
  
 <xref:System.ServiceModel.IClientChannel>Rozhraní však nedefinuje kontrakt služby samotný. Ty jsou deklarovány rozhraním kontraktu služby (obvykle vygenerované z metadat služby pomocí nástroje, jako je například nástroj pro dodávání [metadat třídy ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)). Typy klientů WCF rozšiřuje <xref:System.ServiceModel.IClientChannel> rozhraní a cílové kontrakty služby, aby mohly aplikace volat operace přímo, a mají také přístup ke běhovým funkcím na straně klienta. Vytváření klienta služby WCF poskytuje <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> objekty WCF s informacemi potřebnými k vytvoření času spuštění, který se může připojit k nakonfigurovanému koncovému bodu služby a pracovat s ním.  
  
 Jak už bylo zmíněno dříve, dva typy klientů WCF je třeba nakonfigurovat, aby je bylo možné použít. Nejjednodušší typy klientů WCF jsou objekty, které jsou odvozeny z <xref:System.ServiceModel.ClientBase%601> (nebo <xref:System.ServiceModel.DuplexClientBase%601> Pokud je kontrakt služby duplexní smlouvou). Tyto typy můžete vytvořit pomocí konstruktoru, nakonfigurované programově nebo pomocí konfiguračního souboru a potom zavolat přímo k vyvolání operací služby. Základní přehled <xref:System.ServiceModel.ClientBase%601> objektů najdete v tématu [Přehled klientů WCF](../wcf-client-overview.md).  
  
 Druhý typ je generován v době běhu voláním <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A> metody. Příslušné aplikace s těsnou kontrolou specifických komunikací obvykle používají tento typ klienta, označovaný jako *objekt kanálu klienta*, protože umožňují pružnější interakci než základní klientský čas spuštění a systém kanálu.  
  
## <a name="channel-factories"></a>Továrny kanálů  
 Třída, která je odpovědná za vytvoření základní doby spuštění, která podporuje vyvolání klienta, je <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> Třída. Objekty klienta WCF a objekty kanálu klienta WCF používají <xref:System.ServiceModel.ChannelFactory%601> objekt k vytváření instancí. <xref:System.ServiceModel.ClientBase%601> odvozený objekt klienta zapouzdřuje zpracování objektu pro vytváření kanálů, ale u řady scénářů je naprosto rozumný použít přímo objekt pro vytváření kanálů. Obvyklým scénářem je situace, kdy chcete opakovaně vytvářet nové kanály klienta ze stávajícího objektu pro vytváření. Pokud používáte objekt klienta, můžete získat nadřízený objekt pro vytváření kanálů z objektu klienta WCF voláním <xref:System.ServiceModel.ClientBase%601.ChannelFactory%2A?displayProperty=nameWithType> Vlastnosti.  
  
 Důležité je pamatovat si informace o továrnách kanálů, protože vytvářejí nové instance klientských kanálů pro konfiguraci, které jim byly poskytnuty před voláním <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> . Když zavoláte <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A> (nebo <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> , <xref:System.ServiceModel.ClientBase%601.CreateChannel%2A?displayProperty=nameWithType> nebo jakoukoli operaci na objektu klienta WCF), nemůžete upravit objekt pro vytváření kanálů a očekávat kanály pro různé instance služby, a to i v případě, že pouze měníte adresu cílového koncového bodu. Pokud chcete vytvořit objekt klienta nebo klientský kanál s jinou konfigurací, musíte nejdřív vytvořit nový objekt pro vytváření kanálů.  
  
 Další informace o různých problémech pomocí objektů klienta WCF a kanálů klientů WCF najdete v tématu [přístup ke službám pomocí klienta WCF](accessing-services-using-a-client.md).  
  
 Následující dvě části popisují vytvoření a použití objektů kanálu klienta WCF.  
  
#### <a name="creating-a-new-wcf-client-channel-object"></a>Vytváření nového objektu kanálu klienta WCF  
 Pro ilustraci použití kanálu klienta se vygeneroval následující kontrakt služby.  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 Pokud se chcete připojit ke `ISampleService` službě, použijte rozhraní generovaného kontraktu přímo s objektem pro vytváření kanálů ( <xref:System.ServiceModel.ChannelFactory%601> ). Jakmile vytvoříte a nakonfigurujete továrnu kanálu pro konkrétní kontrakt, můžete zavolat metodu, která <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A> vrátí objekty kanálu klienta, které můžete použít ke komunikaci se `ISampleService` službou.  
  
 Při použití <xref:System.ServiceModel.ChannelFactory%601> třídy s rozhraním kontraktu služby je nutné přetypovat na rozhraní, <xref:System.ServiceModel.IClientChannel> aby bylo možné explicitně otevřít, zavřít nebo přerušit kanál. Aby bylo snazší pracovat s nástrojem, nástroj Svcutil. exe také generuje pomocné rozhraní, které implementuje rozhraní kontraktu služby, a umožňuje <xref:System.ServiceModel.IClientChannel> interakci s infrastrukturou kanálu klienta bez nutnosti přetypování. Následující kód ukazuje definici kanálu pomocníka klienta, který implementuje předchozí kontrakt služby.  
  
 [!code-csharp[C_GeneratedCodeFiles#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#13)]  
  
#### <a name="creating-a-new-wcf-client-channel-object"></a>Vytváření nového objektu kanálu klienta WCF  
 Chcete-li použít klientský kanál pro připojení ke `ISampleService` službě, použijte vygenerované rozhraní kontraktu (nebo pomocnou verzi) přímo s objektem pro vytváření kanálů a předáním typu rozhraní kontraktu jako parametru typu. Jakmile vytvoříte a nakonfigurujete továrnu kanálu pro konkrétní kontrakt, můžete zavolat metodu, která <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> vrátí objekty kanálu klienta, které můžete použít ke komunikaci se `ISampleService` službou.  
  
 Při vytváření objekty kanálu klienta implementují <xref:System.ServiceModel.IClientChannel> a rozhraní kontraktu. Proto je můžete použít přímo k volání operací, které komunikují se službou, která tuto smlouvu podporuje.  
  
 Rozdíl mezi použitím objektů klienta a objektů klientských kanálů je pouze jedním z kontrol a snadného použití pro vývojáře. Mnoho vývojářů, kteří potřebují pracovat s třídami a objekty, bude preferovat použití objektu klienta WCF namísto kanálu klienta WCF.  
  
 Příklad naleznete v tématu [How to: Use a ChannelFactory](how-to-use-the-channelfactory.md).
