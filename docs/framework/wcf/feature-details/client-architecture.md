---
title: Architektura klienta
ms.date: 03/30/2017
ms.assetid: 02624403-0d77-41cb-9a86-ab55e98c7966
ms.openlocfilehash: 6ed00054de45abc23fdd9ad69f61c758f567b973
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64656061"
---
# <a name="client-architecture"></a>Architektura klienta
Aplikace objekty klienta Windows Communication Foundation (WCF) použít k vyvolání operace služby. Toto téma popisuje objekty klienta WCF, kanály WCF klientů a jejich vztahů k základní architektuře kanálu. Základní přehled objekty klienta WCF, najdete v tématu [přehled klientů WCF](../../../../docs/framework/wcf/wcf-client-overview.md). Další informace o vrstvě kanálu najdete v tématu [rozšíření vrstvy kanálu](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md).  
  
## <a name="overview"></a>Přehled  
 Model služby čas spuštění vytvoří klientů WCF, které se skládají z následujících akcí:  
  
- Automaticky generovaného klienta implementace kontraktu služby, která odchozí zprávy se změní volání od kódu aplikace a převede zprávy s odezvami na výstupní parametry a návratové hodnoty, které vaše aplikace může načíst.  
  
- Implementace rozhraní ovládacího prvku (<xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType>), která seskupuje různá rozhraní a poskytuje přístup k ovládání funkcí, zejména možnost Zavřít relace klienta a uvolnění kanál.  
  
- Kanál klienta, která je vytvořená na základě konfigurace nastavení zadané použité vazbou.  
  
 Aplikace můžete vytvořit tyto klienty na vyžádání, buď prostřednictvím <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> nebo tak, že vytvoříte instanci <xref:System.ServiceModel.ClientBase%601> odvozené třídy, jak často jsou generovaná podle [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Tyto třídy připravené vytvořené klienta zapouzdření a delegování pro implementaci kanálu klienta, která je dynamicky vytvářený <xref:System.ServiceModel.ChannelFactory>. Proto jsou kanálu klienta a výrobu kanálu, který vytváří je ústředním bodem týkající se této diskuse.  
  
## <a name="client-objects-and-client-channels"></a>Objekty klienta a klientské kanály  
 Je základní rozhraní klientů WCF <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> rozhraní, které zpřístupňuje základní klientské funkce, jakož i základní komunikační funkce objektu <xref:System.ServiceModel.ICommunicationObject?displayProperty=nameWithType>, funkce kontextu <xref:System.ServiceModel.IContextChannel?displayProperty=nameWithType>a rozšiřitelné chování <xref:System.ServiceModel.IExtensibleObject%601?displayProperty=nameWithType>.  
  
 <xref:System.ServiceModel.IClientChannel> Rozhraní, ale nedefinuje samotné kontraktu služby. Ty jsou deklarovány pomocí rozhraní kontraktu služby (obvykle generují z metadat služby pomocí některého nástroje, například [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)). Typ klienta WCF rozšířit i <xref:System.ServiceModel.IClientChannel> a cílové rozhraní kontraktu služby k umožňují aplikacím přímo a také volání operací mají přístup k funkcím na straně klienta za běhu. Vytvoření klienta WCF poskytuje WCF<xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> objekty s informace potřebné k vytvoření době běhu, které můžete připojit a pracovat s nakonfigurovaný koncový bod služby.  
  
 Jak už bylo zmíněno dříve, musí být nakonfigurované dva typy klienta WCF, než budete moct použít. Nejjednodušší typ klienta WCF jsou objekty, které jsou odvozeny z <xref:System.ServiceModel.ClientBase%601> (nebo <xref:System.ServiceModel.DuplexClientBase%601> Pokud kontrakt služby je duplexního kontraktu). Můžete vytvořit tyto typy pomocí konstruktoru, konfigurují programově, nebo pomocí konfiguračního souboru a pak volat přímo k vyvolání operace služby. Základní přehled <xref:System.ServiceModel.ClientBase%601> objekty, najdete [přehled klientů WCF](../../../../docs/framework/wcf/wcf-client-overview.md).  
  
 Druhý typ je generován za běhu z volání <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A> metody. Aplikace obvykle týká absolutní kontrolu specifika komunikace použít tento typ klienta volána *objekt kanálu klienta*, protože umožňuje více díky přímé interakci než základní klienta za běhu a kanálu systém.  
  
## <a name="channel-factories"></a>Objekty pro vytváření kanálů  
 Třída, která zodpovídá za vytvoření základního běhu, který podporuje volání klienta je <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> třídy. Objekty pomocí kanálu objekty klienta WCF a klienta WCF <xref:System.ServiceModel.ChannelFactory%601> objekt pro vytváření instancí; <xref:System.ServiceModel.ClientBase%601> objekt odvozené klienta zapouzdřuje zpracování objekt pro vytváření kanálů, ale pro řadu scénářů je naprosto vhodné použít objekt pro vytváření kanálů přímo. Běžným scénářem je, pokud budete chtít opakovaně vytvořit nového klienta kanály v existujícím objektu pro vytváření. Pokud používáte objekt klienta, můžete získat výrobu kanálu z objektu klienta WCF pomocí volání <xref:System.ServiceModel.ClientBase%601.ChannelFactory%2A?displayProperty=nameWithType> vlastnost.  
  
 Důležité informace o vytváření kanálů je, že vytvořit nové instance klientské kanály pro konfiguraci poskytuje k nim před voláním <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType>. Jakmile zavoláte <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A> (nebo <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.ClientBase%601.CreateChannel%2A?displayProperty=nameWithType>, nebo všechny operace na objektu klienta WCF), nelze upravit objekt pro vytváření kanálů a můžete očekávat kanály pro instance různé služby, i když měníte pouze cílová adresa koncového bodu. Pokud chcete vytvořit objekt klienta nebo kanálu klienta s jinou konfiguraci, musíte nejprve vytvořit nový objekt pro vytváření kanálů.  
  
 Další informace o různých problémů pomocí objekty klienta WCF a kanály klientů WCF najdete v tématu [přístup ke službám pomocí klienta WCF](../../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md).  
  
 V následujících dvou částech vytváření a používání objekty kanálu klienta WCF.  
  
#### <a name="creating-a-new-wcf-client-channel-object"></a>Vytvoření nového objektu kanálu klienta WCF  
 Pro ilustraci použití kanálu klienta, se předpokládá, že byl vytvořen kontrakt následující služby.  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 Pro připojení k `ISampleService` služby, použijte rozhraní generovaného kontraktu přímo pomocí objektu pro vytváření kanálů (<xref:System.ServiceModel.ChannelFactory%601>). Po vytvoření a konfigurace objektu pro vytváření kanálů pro konkrétní kontrakt, můžete volat <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A> metoda vrátí objekty kanálu, které můžete použít ke komunikaci s klienta `ISampleService` služby.  
  
 Při použití <xref:System.ServiceModel.ChannelFactory%601> třídy pomocí rozhraní kontraktu služby, musíte přetypovat <xref:System.ServiceModel.IClientChannel> rozhraní explicitně otevření, zavření nebo přerušení kanálu. Aby bylo snazší pracovat, nástroje Svcutil.exe také vygeneruje rozhraní pomocné rutiny, která implementuje oba rozhraní servisní smlouvy a <xref:System.ServiceModel.IClientChannel> umožňuje interakci s vaší stávající infrastrukturou kanálu klienta bez nutnosti přetypování. Následující kód znázorňuje definici kanálu pomocné rutiny klienta, který implementuje předchozí kontrakt služby.  
  
 [!code-csharp[C_GeneratedCodeFiles#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#13)]  
  
#### <a name="creating-a-new-wcf-client-channel-object"></a>Vytvoření nového objektu kanálu klienta WCF  
 Použití kanálu klienta pro připojení k `ISampleService` služeb, použijte rozhraní generovaného kontraktu (nebo verze pomocné rutiny) přímo pomocí objektu pro vytváření kanálů, předejte typ rozhraní kontraktu jako parametr typu. Jakmile objektu pro vytváření kanálů pro konkrétní kontrakt bylo vytvořeno a nakonfigurováno, můžete volat <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> metoda vrátí objekty kanálu, které můžete použít ke komunikaci s klienta `ISampleService` služby.  
  
 Při implementaci objekty kanálu klienta <xref:System.ServiceModel.IClientChannel> a interface kontraktu. Proto je můžete použít přímo k volání operací, které pracují se službou, která podporuje tento kontrakt.  
  
 Rozdíl mezi použitím klienta a klient objekty kanálu je pouze jeden ovládací prvek a snadnějším použitím pro vývojáře. Mnoho vývojářů, kteří jste zběhlí v práci s třídami a objekty se dávají přednost používání objektu klienta WCF místo kanálu klienta WCF.  
  
 Příklad najdete v tématu [jak: Používání ChannelFactory](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md).
