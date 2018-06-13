---
title: Rozšíření ServiceHost a vrstva modelu služby
ms.date: 03/30/2017
helpviewer_keywords:
- extending service models [WCF]
ms.assetid: 954c138a-1cd0-45a0-8abe-e4d2b8ff5400
ms.openlocfilehash: 9e08b5b7b11848262d2cb7b6ed5715799d597889
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33803473"
---
# <a name="extending-servicehost-and-the-service-model-layer"></a>Rozšíření ServiceHost a vrstva modelu služby
Vrstva modelu služby je zodpovědná za stahování příchozí zprávy mimo základní kanály, převedena do volání metod v kódu aplikace a odesílání výsledky zpět k volajícímu. Rozšíření modelů služby upravit nebo jsou implementovány provádění nebo komunikace chování a funkce zahrnující klienta nebo dispečera funkce, vlastní chování, zprávu a parametr zachycení a další funkce rozšiřitelnost.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Rozšíření klientů](../../../../docs/framework/wcf/extending/extending-clients.md)  
 Popisuje rozhraní, které mohou zachytávat a upravit modul runtime klienta a také třídy, do kterých můžete vložit vlastními rozšířeními v klientských aplikacích. Můžete například provést protokolování zpráv vlastní klienta, proveďte vlastní zprávu při serializaci a tak dále.  
  
 [Rozšíření dispečerů](../../../../docs/framework/wcf/extending/extending-dispatchers.md)  
 Popisuje rozhraní, které mohou zachytávat a upravit běh služby a také třídy, do kterých můžete vložit vlastní rozšíření aplikace služby. Například můžete provádět vlastní službu protokolování, ověření na straně služby zprávy, vlastní odeslání a podobně.  
  
 [Rozšiřitelné objekty](../../../../docs/framework/wcf/extending/extensible-objects.md)  
 Popisuje pět rozšiřitelné objekty a <xref:System.ServiceModel.IExtensibleObject%601> vzor. Vzor extensible objektu se používá buď rozšířit existující třídy runtime s novými funkcemi nebo přidat nový stav na objekt. Rozšíření, které jsou připojené k jednomu rozšiřitelné objekty, aktivujte velmi různých fází zpracování pro přístup k sdílení stavu a funkce, které jsou připojené k běžné extensible objekt, který bude mít přístup k chování.  
  
 [Konfigurace a rozšíření modulu runtime pomocí chování](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)  
 Chcete-li změnit nastavení v nebo vložit rozšíření v modulu runtime WCF, použijte chování. WCF zahrnuje implementované systému chování pro řízení omezení, vytváření instancí a mnoho dalších aspektů služby a operace. Tato část popisuje postup vytvoření vlastního vlastní chování a jak je k dispozici pro použití obou prostřednictvím kódu programu a pomocí konfiguračních souborů.  
  
 [Rozšíření hostování pomocí ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)  
 Popisuje, jak rozšířit <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType>, <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>a použít <xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=nameWithType> třídy k přizpůsobení hostitelské prostředí.  
  
## <a name="reference"></a>Odkaz  
  
## <a name="related-sections"></a>Související oddíly
