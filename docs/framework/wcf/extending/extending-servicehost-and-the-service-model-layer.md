---
title: Rozšíření ServiceHost a vrstva modelu služby
ms.date: 03/30/2017
helpviewer_keywords:
- extending service models [WCF]
ms.assetid: 954c138a-1cd0-45a0-8abe-e4d2b8ff5400
ms.openlocfilehash: e370316cd121f49953e00e83dfc9d2aec17de1e8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795733"
---
# <a name="extending-servicehost-and-the-service-model-layer"></a>Rozšíření ServiceHost a vrstva modelu služby
Vrstva modelu služby zodpovídá za příjem příchozích zpráv ze základních kanálů, jejich překlad na vyvolání metod v kódu aplikace a odesílání výsledků zpět volajícímu. Rozšíření modelu služby upraví nebo implementují chování nebo chování komunikace a funkce zahrnující funkce klienta nebo dispečera, vlastní chování, zachycení zprávy a parametry a další funkce rozšíření.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Rozšíření klientů](extending-clients.md)  
 Popisuje rozhraní, která mohou zachytit a změnit modul runtime klienta, a také třídy, do kterých můžete vkládat vlastní rozšíření v klientských aplikacích. Můžete například provádět vlastní protokolování zpráv klienta, provádět vlastní serializaci zpráv a tak dále.  
  
 [Rozšíření dispečerů](extending-dispatchers.md)  
 Popisuje rozhraní, která mohou zachytit a změnit modul runtime služby a také třídy, do kterých můžete vkládat vlastní rozšíření v aplikacích služeb. Můžete například provádět vlastní protokolování služby, ověřování zpráv na straně služby, vlastní odesílání a tak dále.  
  
 [Rozšiřitelné objekty](extensible-objects.md)  
 Popisuje pět rozšiřitelných objektů a <xref:System.ServiceModel.IExtensibleObject%601> vzor. Vzor rozšiřitelného objektu se používá pro rozšiřující existující běhové třídy s novými funkcemi nebo pro přidání nového stavu do objektu. Rozšíření, která jsou připojená k jednomu z rozšiřitelných objektů, umožňují chování ve velmi různých fázích zpracování pro přístup ke sdílenému stavu a funkčnosti připojenému ke společnému rozšiřitelnému objektu, ke kterému mají přístup.  
  
 [Konfigurace a rozšíření modulu runtime pomocí chování](configuring-and-extending-the-runtime-with-behaviors.md)  
 Chcete-li změnit nastavení nebo vložení rozšíření v modulu runtime služby WCF, použijte chování. Služba WCF zahrnuje chování implementované systémem pro řízení omezování, vytváření instancí a mnoho dalších aspektů služeb a operací. V této části se dozvíte, jak vytvořit vlastní chování a jak je zpřístupnit pro použití programově i v konfiguračních souborech.  
  
 [Rozšíření hostování pomocí ServiceHostFactory](extending-hosting-using-servicehostfactory.md)  
 V této části <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType> <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> najdetepopis<xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=nameWithType> postupu při rozšiřování, a používání tříd k přizpůsobení hostitelského prostředí.  
  
## <a name="reference"></a>Reference  
  
## <a name="related-sections"></a>Související oddíly
