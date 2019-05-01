---
title: Rozšíření ServiceHost a vrstva modelu služby
ms.date: 03/30/2017
helpviewer_keywords:
- extending service models [WCF]
ms.assetid: 954c138a-1cd0-45a0-8abe-e4d2b8ff5400
ms.openlocfilehash: 9e08b5b7b11848262d2cb7b6ed5715799d597889
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991767"
---
# <a name="extending-servicehost-and-the-service-model-layer"></a>Rozšíření ServiceHost a vrstva modelu služby
Vrstva modelu služby je zodpovědná za přesun příchozí zprávy z podkladové kanály, překládá na volání metod v kódu aplikace a odesílá výsledky zpět do volajícího. Rozšíření modelů služeb změnit nebo implementovat provádění nebo chování komunikace a funkce zahrnující funkce klienta nebo dispečer, vlastní chování, zprávy a parametr zachycení a další funkce rozšíření.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Rozšíření klientů](../../../../docs/framework/wcf/extending/extending-clients.md)  
 Popisuje rozhraní, které mohou zachytávat a změnit modul runtime klienta, stejně jako třídy, do kterých můžete vložit vlastní rozšíření v klientských aplikacích. Můžete například provádět protokolování zpráv vlastního klienta, proveďte serializace vlastní zprávu a podobně.  
  
 [Rozšíření dispečerů](../../../../docs/framework/wcf/extending/extending-dispatchers.md)  
 Popisuje rozhraní, které mohou zachytávat a změnit modul runtime služby, stejně jako třídy, do kterých můžete vložit vlastní rozšíření aplikace služby. Můžete například provádět vlastní služby protokolování, ověřovacích zpráv na straně služby, vlastní odesílání a tak dále.  
  
 [Rozšiřitelné objekty](../../../../docs/framework/wcf/extending/extensible-objects.md)  
 Popisuje pět rozšiřitelné objekty a <xref:System.ServiceModel.IExtensibleObject%601> vzor. Vzor rozšiřitelném objektu se používá k buď rozšířit existující třídy modulu runtime s novými funkcemi a přidat nový stav objektu. Rozšíření, připojený k jednomu rozšiřitelné objekty povolit chování na velmi různé fáze zpracování pro přístup k sdílený stav a připojené k běžné rozšiřitelném objektu, který bude mít přístup k funkci.  
  
 [Konfigurace a rozšíření modulu runtime pomocí chování](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)  
 Pokud chcete změnit nastavení v nebo vložit rozšíření v modulu runtime WCF, použijete chování. WCF obsahuje systému implementované chování pro řízení omezování, vytváření instancí a mnoho dalších aspektů služby a operace. Tato část popisuje, jak vytvářet vlastní vlastní chování, jak je k dispozici pro použití obou prostřednictvím kódu programu a pomocí konfiguračních souborů.  
  
 [Rozšíření hostování pomocí ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)  
 Popisuje, jak rozšířit <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType>, <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>a použít <xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=nameWithType> třídy k přizpůsobení prostředí hostitele.  
  
## <a name="reference"></a>Odkaz  
  
## <a name="related-sections"></a>Související oddíly
