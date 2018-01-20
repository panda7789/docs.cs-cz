---
title: "Konfigurační schéma služby WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c282aeb5-91f0-4522-8e2f-704c1ef3651f
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7286793d6b2ad94c656dd37cdcc5fe1b0ab85660
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="wcf-configuration-schema"></a>Konfigurační schéma služby WCF
[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]konfigurace – elementy umožňují nakonfigurovat [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] služby a klientské aplikace. Můžete použít [nástroj Configuration Editor (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) vytvářet a upravovat konfigurační soubory pro klienty a služby. Vzhledem k tomu, že konfigurační soubory, které jsou formátovány jako XML, musí být nebude znají XML Pokud chcete ručně upravovat pomocí textového editoru. Jinak můžete jej spustit do problémy jako k unfound značky elementu XML nebo atributu. Důvodem je, že značky elementu XML a atributy jsou malá a velká písmena.  
  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] Podle konfigurace systému <xref:System.Configuration> oboru názvů. Proto můžete použít standardní funkce poskytované službou <xref:System.Configuration> oboru názvů, jako např. konfigurace zámku, šifrování a slučování ke zvýšení zabezpečení vaší aplikace a její konfiguraci. Další informace o těchto konceptech naleznete v následujících tématech.  
  
 [Informace o konfiguraci šifrování](http://go.microsoft.com/fwlink/?LinkId=95337)  
  
 [Nastavení uzamčení](http://go.microsoft.com/fwlink/?LinkId=95338)  
  
 Tato část popisuje všechny možné hodnoty každé položky konfigurace a jak komunikuje s jinými prvky konfigurace WCF. Následující mapa znázorňuje schéma konfigurace WCF.  
  
 ![WCF Configuration Schema](../../../../../docs/framework/configure-apps/file-schema/wcf/media/orcasconfigschema.gif "OrcasConfigSchema")  
  
> [!CAUTION]
>  Měli byste chránit [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] konfigurační oddíly funkce v konfigurační soubory aplikace (app.config) s odpovídající řízení přístupu jsou uvedené (ACL) aby se zabránilo všechny potenciální bezpečnostní hrozby.  Měli byste si například ověřit, že pouze na příslušné osoby lze zobrazit nebo upravit nastavení zabezpečení na vazby aplikace nebo v části modelu služby konfiguračního souboru pro službu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [\<system.serviceModel>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
 Popisuje `ServiceModel` elementu.  
  
 [\<system.serviceModel.activation>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)  
 Konfiguruje nástroj SMSvcHost.exe.  
  
 [\<system.runtime.serialization>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)  
 Element nejvyšší úrovně pro nastavení možností při použití serializátorů, jako <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
## <a name="related-sections"></a>Související oddíly  
 [Konfigurace aplikací pro Windows Communication Foundation](http://msdn.microsoft.com/library/13cb368e-88d4-4c61-8eed-2af0361c6d7a)  
 Popisuje postup konfigurace [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] služeb a klientů.
