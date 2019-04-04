---
title: Konfigurační schéma služby WCF
ms.date: 03/30/2017
ms.assetid: c282aeb5-91f0-4522-8e2f-704c1ef3651f
ms.openlocfilehash: baea1e49bce10054530afa5b6f282023d5ceb981
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2019
ms.locfileid: "58463329"
---
# <a name="wcf-configuration-schema"></a>Konfigurační schéma služby WCF
Windows Communication Foundation (WCF) konfigurační prvky umožňují nakonfigurovat služeb a klientských aplikací WCF. Můžete použít [nástroj Configuration Editor (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) vytvářet a upravovat konfigurační soubory pro klienty a služby. Protože konfigurační soubory jsou formátovány jako XML, musíte znát XML Pokud budete chtít ručně upravovat pomocí textového editoru. Jinak můžete jej spustit do problémy jako k unfound značky elementu XML nebo atributu. Důvodem je, že značky elementu XML a atributy jsou malá a velká písmena.  
  
 Systém konfigurace WCF je založen na <xref:System.Configuration> oboru názvů. Proto můžete použít všechny funkce úrovně standard poskytuje <xref:System.Configuration> obor názvů, jako např. konfigurace zámku, šifrování a slučování ke zvýšení zabezpečení aplikace a její konfiguraci. Další informace o těchto konceptech naleznete v následujících tématech.  
  
 [Informace o konfiguraci šifrování](https://go.microsoft.com/fwlink/?LinkId=95337)  
  
 [Nastavení uzamčení](https://go.microsoft.com/fwlink/?LinkId=95338)  
  
 Tato část popisuje všechny možné hodnoty každé položky konfigurace a interakci s ostatními prvky konfigurace WCF. Následující mapa znázorňuje schéma konfigurace služby WCF:  
  
 ![Diagram zobrazující průběh konfigurační schéma služby WCF.](./media/index/windows-communication-foundation-configuration-schema.gif)  
  
> [!CAUTION]
>  Měli byste chránit WCF konfigurační oddíly funkce v konfigurační soubory aplikace (app.config) s odpovídající řízení přístupu jsou uvedeny (ACL) aby všechny potenciální ohrožení zabezpečení.  Například by měl Ujistěte se, že pouze na příslušné osoby můžete upravit nebo přistoupit k nastavení zabezpečení v aplikaci vazby nebo model oddílu služby konfiguračního souboru pro službu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [\<system.serviceModel>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
 Popisuje `ServiceModel` elementu.  
  
 [\<system.serviceModel.activation>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)  
 Konfiguruje nástroj SMSvcHost.exe.  
  
 [\<system.runtime.serialization>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)  
 Element nejvyšší úrovně pro nastavení možností při použití serializátory, jako <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
## <a name="related-sections"></a>Související oddíly  
 [Konfigurace aplikací Windows Communication Foundation](../../../wcf/configuring-services.md)  
 Popisuje postup konfigurace služby WCF a klienty.
