---
title: Architektura klienta
ms.date: 03/30/2017
ms.assetid: 02624403-0d77-41cb-9a86-ab55e98c7966
ms.openlocfilehash: 4ced24f370e2ab54528c6adb2b3617d3d849e745
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="client-architecture"></a>Architektura klienta
Aplikace používaná k volání operací služby objekty klienta Windows Communication Foundation (WCF). Toto téma popisuje objekty klienta WCF, kanály klienta WCF a jejich vztahů s základní architektury kanálu. Základní přehled objekty klienta WCF, najdete v tématu [klienta WCF – přehled](../../../../docs/framework/wcf/wcf-client-overview.md). Další informace o vrstvy kanálu najdete v tématu [rozšíření vrstvy kanálu](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md).  
  
## <a name="overview"></a>Přehled  
 Model služby běh vytvoří klienti WCF, které se skládají z následujících akcí:  
  
-   Automaticky generovaného klienta implementace kontraktu služby, který změní volání z kódu vaší aplikace do zpráv a změní odpovědi na zprávy do výstupní parametry a návratové hodnoty, které vaše aplikace může načíst.  
  
-   Implementace rozhraní ovládacího prvku (<xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType>), skupiny společně různé rozhraní a poskytuje přístup k ovládání funkcí, zejména možnost ukončení relace klienta a uvolnění kanál.  
  
-   Klient kanálu, který je založený na základě konfigurace nastavení určeného použité vazby.  
  
 Aplikace můžete vytvořit tyto klienty na vyžádání, buď prostřednictvím <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> nebo tak, že vytvoříte instanci <xref:System.ServiceModel.ClientBase%601> odvozené třídy, jako je generován [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Tyto třídy klienta vytvořené připravené pro zapouzdření a delegovat na implementace kanálu klienta, který je sestavený dynamicky podle <xref:System.ServiceModel.ChannelFactory>. Proto jsou kanálem klienta a kanálu, který vytváří je ústředním bodem týkající se toto pojednání.  
  
## <a name="client-objects-and-client-channels"></a>Objekty klienta a klient kanály  
 Základní rozhraní WCF klientů je <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> rozhraní, které zpřístupňuje základní funkce klienta a také funkce objekt základní komunikace <xref:System.ServiceModel.ICommunicationObject?displayProperty=nameWithType>, funkce kontextu <xref:System.ServiceModel.IContextChannel?displayProperty=nameWithType>a rozšiřitelné chování <xref:System.ServiceModel.IExtensibleObject%601?displayProperty=nameWithType>.  
  
 <xref:System.ServiceModel.IClientChannel> Rozhraní, ale nedefinuje kontraktu služby, sám sebe. Ty jsou deklarovaná rozhraní kontraktu služby (obvykle vygeneruje z metadat služby pomocí nástroje, například [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)). Typy klienta WCF rozšířit obě <xref:System.ServiceModel.IClientChannel> a cílové rozhraní kontraktu služby umožnit aplikacím volání operací přímo a také mít přístup k funkcím runtime klienta. Vytvoření klienta WCF poskytuje WCF<xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> objekty s informace potřebné k vytvoření dobu spuštění, které se můžete připojit a interakci s koncovým bodem konfigurovaných služeb.  
  
 Jak už bylo zmíněno dříve, musí být nakonfigurované dva typy klienta WCF, abyste mohli používat. Nejjednodušší typy klienta WCF jsou objekty, které jsou odvozeny od <xref:System.ServiceModel.ClientBase%601> (nebo <xref:System.ServiceModel.DuplexClientBase%601> Pokud duplexního kontraktu kontrakt služby). Můžete vytvořit tyto typy pomocí konstruktoru nakonfigurované prostřednictvím kódu programu, nebo pomocí konfiguračního souboru a pak volat přímo k vyvolání operace služby. Pro základní přehled <xref:System.ServiceModel.ClientBase%601> objekty, najdete v části [klienta WCF – přehled](../../../../docs/framework/wcf/wcf-client-overview.md).  
  
 Druhý typ je vygenerován v době běhu volání <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A> metoda. Aplikace problémem s přísnou kontrolu specifika komunikace obvykle používají tento typ klienta, názvem *objekt kanálu klienta*, protože umožňuje více přímé interakce než základní běhu klienta a kanál systém.  
  
## <a name="channel-factories"></a>Objekty factory kanálu  
 Třída, která zodpovídá za vytvoření základní běh, který podporuje volání klienta je <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> třídy. Objekty klienta WCF a klienta WCF kanálu pomocí objektů <xref:System.ServiceModel.ChannelFactory%601> objekt k vytvoření instance; <xref:System.ServiceModel.ClientBase%601> objekt odvozené klienta zapouzdří zpracování objektu pro vytváření kanálu, ale pro různé scénáře je perfektně vhodné použít Postup kanálu přímo. Běžné scénáře je, pokud chcete opakovaně vytvořit nového klienta kanály z existujícím objektu pro vytváření. Pokud používáte objekt klienta, můžete získat základní kanálu z objektu klienta WCF voláním <xref:System.ServiceModel.ClientBase%601.ChannelFactory%2A?displayProperty=nameWithType> vlastnost.  
  
 Je důležité si pamatovat o objekty Factory kanál je, že se vytvořit nové instance třídy klienta kanály pro konfiguraci poskytuje k nim před voláním <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType>. Jakmile zavoláte <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A> (nebo <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.ClientBase%601.CreateChannel%2A?displayProperty=nameWithType>, nebo všechny operace u objektu klienta WCF), nemůžete upravovat vytváření kanálů a můžete očekávat kanály pro instance různé služby, i když měníte jenom cílová adresa koncového bodu. Pokud chcete vytvořit objekt klienta nebo kanálem klienta s jinou konfiguraci, je nutné nejprve vytvořit novou kanálu.  
  
 Další informace o různých problémy s objekty klienta WCF a kanály klienta WCF najdete v tématu [přístup k službám pomocí klienta WCF](../../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md).  
  
 Následující dvě části popisují vytvoření a použití objekty kanálu klienta WCF.  
  
#### <a name="creating-a-new-wcf-client-channel-object"></a>Vytvoření nového objektu kanálem klienta WCF  
 Pro ilustraci použití kanálu klienta, předpokládá, že byla vygenerována následující kontrakt služby.  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 Pro připojení k `ISampleService` služby, použijte rozhraní vygenerovaný kontrakt přímo pomocí postupu kanálu (<xref:System.ServiceModel.ChannelFactory%601>). Jakmile vytvoříte a nakonfigurujete kanálu pro konkrétní kontrakt, můžete zavolat <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A> metoda vrátí klienta kanál objekty, které můžete použít ke komunikaci s `ISampleService` služby.  
  
 Při použití <xref:System.ServiceModel.ChannelFactory%601> – třída pomocí rozhraní kontraktu služby, musíte přetypovat <xref:System.ServiceModel.IClientChannel> rozhraní explicitně otevřít, zavřít nebo přerušení kanál. Aby bylo snazší s ním pracovat, nástroje Svcutil.exe rovněž vygeneruje rozhraní pomocné rutiny, který implementuje rozhraní služby kontrakt rozhraní a <xref:System.ServiceModel.IClientChannel> umožnit komunikovat s infrastrukturou kanálu klienta bez nutnosti přetypovat. Následující kód ukazuje definici kanálu klienta pomocné rutiny, který implementuje předchozí kontrakt služby.  
  
 [!code-csharp[C_GeneratedCodeFiles#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#13)]  
  
#### <a name="creating-a-new-wcf-client-channel-object"></a>Vytvoření nového objektu kanálem klienta WCF  
 K použití kanálu klienta pro připojení k `ISampleService` služby, použijte rozhraní vygenerovaný kontraktu (nebo verze pomocné rutiny) přímo s kanálu, předávání typu rozhraní kontraktu jako parametr typu. Jakmile kanálu pro konkrétní kontrakt byla vytvořena a nakonfigurována, můžete zavolat <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> metoda vrátí klienta kanál objekty, které můžete použít ke komunikaci s `ISampleService` služby.  
  
 Při vytváření implementovat objekty kanálu klienta <xref:System.ServiceModel.IClientChannel> a rozhraní kontraktu. Proto je můžete použít přímo k volání operací, které pracují se služba, která podporuje tohoto kontraktu.  
  
 Rozdíl mezi použitím objekty klienta a objekty kanálu klienta je jenom jeden z ovládacího prvku a snadné použití pro vývojáře. Celá řada vývojářů, kteří pohodlně pracovat se tříd a objektů bude dávají přednost používání objekt klienta WCF namísto kanálu klienta WCF.  
  
 Příklad, naleznete v části [postupy: použití třídy ChannelFactory](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md).
