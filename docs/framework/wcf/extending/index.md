---
title: Rozšíření WCF
ms.date: 03/30/2017
helpviewer_keywords:
- WCF, extensibility
- extensibility [WCF]
- Windows Communication Foundation, extensibility
ms.assetid: c145e2f6-f402-41f5-8b5a-eee03978737b
ms.openlocfilehash: 037182a3cb105f544e15a05f955c142ba57f62f3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795535"
---
# <a name="extending-wcf"></a>Rozšíření WCF
Windows Communication Foundation (WCF) umožňuje upravit a roztáhnout komponenty doby běhu pro přesné řízení a rozšiřování aplikací založených na službách. Témata v této části se podrobněji týkají architektury rozšiřitelnosti. Další informace o základním programování naleznete v tématu [Základní programování WCF](../basic-wcf-programming.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Rozšíření ServiceHost a vrstva modelu služby](extending-servicehost-and-the-service-model-layer.md)  
 Vrstva modelu služby zodpovídá za příjem příchozích zpráv ze základních kanálů, jejich překlad na vyvolání metod v kódu aplikace a odesílání výsledků zpět volajícímu.  Rozšíření modelu služby mění nebo implementují chování a funkce pro komunikaci, včetně funkcí dispečerů, vlastního chování, zachycení zpráv a parametrů a dalších funkcí rozšiřitelnosti.  
  
 [Rozšíření vazeb](extending-bindings.md)  
 Vazby jsou objekty, které popisují údaje o komunikaci požadované pro připojení ke koncovému bodu. Rozšíření vazby nebo vlastní vazby implementují vlastní komunikační funkce vyžadované pro podporu funkcí aplikace.  
  
 [Rozšíření vrstvy kanálu](extending-the-channel-layer.md)  
 Vrstva kanálu je umístěná pod vrstvou modelu služby a zodpovídá za výměnu zpráv mezi klienty a službami. Rozšíření kanálů můžou implementovat nové funkce protokolu, jako je zabezpečení. Rozšíření kanálů také přenosové funkce, jako je například implementace nového síťového přenosu, který bude obsahovat zprávy protokolu SOAP.  
  
 [Rozšíření zabezpečení](extending-security.md)  
 Zabezpečení ve službě WCF se skládá z bezpečnostních přenosů (integrity, důvěrnosti a ověřování), řízení přístupu (autorizace) a auditování. Třídy nalezené v `IdentityModel` oboru názvů jsou používány WCF pro řízení přístupu. Princip architektury zabezpečení vám umožní vytvořit vlastní typy deklarací identity, které budou vyhovovat vlastním systémům řízení přístupu.  
  
 [Rozšíření systému metadat](extending-the-metadata-system.md)  
 Systém metadat WCF je skupina tříd a rozhraní, která reprezentují metadata potřebná k implementaci aplikací založených na službách. Upravte nebo rozšíříte třídy nebo implementujte a konfigurujte rozhraní pro export a import vlastních metadat, jako jsou rozšíření jazyka WSDL (Web Services Description Language) nebo vlastní kontrolní výrazy WS-PolicyAttachments.  
  
 [Rozšiřování kodérů a serializátorů](extending-encoders-and-serializers.md)  
 Kodéry a serializátory převádějí data z jednoho formuláře do druhého. Témata v této části popisují, jak tyto třídy rozšíříte tak, aby splňovaly speciální požadavky.  
  
## <a name="reference"></a>Reference  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.IdentityModel.Tokens>  
  
## <a name="related-sections"></a>Související oddíly  
 [Základní programování WCF](../basic-wcf-programming.md)  
  
 [Podrobnosti o funkcích WCF](../feature-details/index.md)  
  
 [Pokyny a osvědčené postupy](../guidelines-and-best-practices.md)
