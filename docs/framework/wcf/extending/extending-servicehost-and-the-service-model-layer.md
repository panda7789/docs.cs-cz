---
title: "Rozšíření ServiceHost a vrstva modelu služby"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- extending service models [WCF]
ms.assetid: 954c138a-1cd0-45a0-8abe-e4d2b8ff5400
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5c73af3b9187fa5365d7ea99474ea182d5f5ae86
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
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
 Pokud chcete změnit nastavení na nebo vložit rozšíření v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modul runtime, používáte chování. WCF zahrnuje implementované systému chování pro řízení omezení, vytváření instancí a mnoho dalších aspektů služby a operace. Tato část popisuje postup vytvoření vlastního vlastní chování a jak je k dispozici pro použití obou prostřednictvím kódu programu a pomocí konfiguračních souborů.  
  
 [Rozšíření hostování pomocí ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)  
 Popisuje, jak rozšířit <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType>, <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>a použít <xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=nameWithType> třídy k přizpůsobení hostitelské prostředí.  
  
## <a name="reference"></a>Odkaz  
  
## <a name="related-sections"></a>Související oddíly
