---
title: Rozšíření WCF
ms.date: 03/30/2017
helpviewer_keywords:
- WCF, extensibility
- extensibility [WCF]
- Windows Communication Foundation, extensibility
ms.assetid: c145e2f6-f402-41f5-8b5a-eee03978737b
ms.openlocfilehash: 24ad74f04a3ac31d0b0d0d87f0d74f88c0521f50
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768716"
---
# <a name="extending-wcf"></a>Rozšíření WCF
Windows Communication Foundation (WCF) umožňuje upravit a rozšířit komponenty běhu lze přesně řídit a rozšířit aplikace založené na službách. Témata v této části přejděte do hloubky o architektuře rozšiřitelnosti. Další informace o základní programování naleznete v tématu [základní programování WCF](../../../../docs/framework/wcf/basic-wcf-programming.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Rozšíření ServiceHost a vrstva modelu služby](../../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md)  
 Vrstva modelu služby je zodpovědná za přesun příchozí zprávy z podkladové kanály, překládá na volání metod v kódu aplikace a odesílá výsledky zpět do volajícího.  Rozšíření modelů služeb změnit nebo implementovat provádění nebo chování komunikace a funkce zahrnující dispečer funkce, vlastní chování, zpráv a parametr zachycení a další funkce rozšíření.  
  
 [Rozšíření vazeb](../../../../docs/framework/wcf/extending/extending-bindings.md)  
 Vazby jsou objekty, které popisují podrobnosti o komunikaci požadované pro připojení na koncový bod. Rozšíření vazby nebo vlastních vazeb implementovat vlastní komunikační funkce potřebné k podpoře funkce aplikace.  
  
 [Rozšíření vrstvy kanálu](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md)  
 Vrstvy kanálu umístěná pod vrstva modelu služby a je zodpovědný za výměnu zpráv mezi klienty a služby. Rozšíření kanálu můžete implementovat nové funkce protokolu, jako je zabezpečení. Rozšíření kanál přenosu také funkce, jako je například implementace nového síťového přenosu přenášet zprávy protokolu SOAP.  
  
 [Rozšíření zabezpečení](../../../../docs/framework/wcf/extending/extending-security.md)  
 Zabezpečení ve službě WCF se skládá z přenosu zabezpečení (integrity, utajení a ověřování), řízení přístupu (autorizace) a auditování. Třídy součástí `IdentityModel` oboru názvů používají WCF pro řízení přístupu. Pochopení architektury zabezpečení umožňuje vytvoření vlastní deklarace typů tak, aby vyhovovaly systémy řízení přístupu vlastní.  
  
 [Rozšíření systému metadat](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)  
 Metadata systému WCF je skupina třídy a rozhraní, které představují metadata jsou požadovaná k implementaci aplikací založené na službách. Upravit nebo rozšířit třídy nebo implementovat a nakonfigurovat rozhraní pro export a import vlastních metadat – například rozšíření webové služby WSDL (Description Language) nebo vlastní WS-PolicyAttachments kontrolní výrazy.  
  
 [Rozšiřování kodérů a serializátorů](../../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md)  
 Kodérů a serializátorů přeložit data z jednoho formuláře. Témata v této části popíšeme, jak rozšířit zadané třídy zvláštní požadavky.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.IdentityModel.Tokens>  
  
## <a name="related-sections"></a>Související oddíly  
 [Základní programování WCF](../../../../docs/framework/wcf/basic-wcf-programming.md)  
  
 [Podrobnosti o funkcích WCF](../../../../docs/framework/wcf/feature-details/index.md)  
  
 [Pokyny a osvědčené postupy](../../../../docs/framework/wcf/guidelines-and-best-practices.md)
