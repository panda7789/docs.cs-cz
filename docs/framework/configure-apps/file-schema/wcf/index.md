---
title: Konfigurační schéma služby WCF
ms.date: 03/30/2017
ms.assetid: c282aeb5-91f0-4522-8e2f-704c1ef3651f
ms.openlocfilehash: 866b0639f4391e1898bbe36e458df87e3c24bfff
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "77448656"
---
# <a name="wcf-configuration-schema"></a>Konfigurační schéma služby WCF
Konfigurační prvky Windows Communication Foundation (WCF) umožňují nakonfigurovat službu WCF a klientské aplikace. Pomocí [nástroje Configuration Editor (SvcConfigEditor. exe)](../../../wcf/configuration-editor-tool-svcconfigeditor-exe.md) můžete vytvářet a upravovat konfigurační soubory pro klienty a služby. Vzhledem k tomu, že konfigurační soubory jsou formátovány jako XML, musíte být obeznámeni s XML, pokud je chcete ručně upravovat pomocí textového editoru. Jinak můžete jej spustit do problémy jako k unfound značky elementu XML nebo atributu. Důvodem je, že značky elementu XML a atributy jsou malá a velká písmena.  
  
 Konfigurační systém WCF je založen na <xref:System.Configuration> oboru názvů. Proto můžete použít všechny standardní funkce poskytované <xref:System.Configuration> oborem názvů, například uzamykání konfigurace, šifrování a sloučení, a zvýšit tak zabezpečení vaší aplikace a její konfigurace. Další informace o těchto konceptech najdete v následujících tématech.  
  
 [Šifrování informací o konfiguraci](https://docs.microsoft.com/previous-versions/aspnet/53tyfkaw(v=vs.100))  
  
 [Uzamykání nastavení konfigurace](https://docs.microsoft.com/previous-versions/aspnet/55th21y4(v=vs.100))  
  
 Tato část popisuje všechny možné hodnoty každé položky konfigurace a způsob, jakým komunikuje s ostatními konfiguračními prvky služby WCF. Následující mapa znázorňuje schéma konfigurace WCF:  
  
 ![Diagram, který zobrazuje schéma konfigurace WCF.](./media/index/windows-communication-foundation-configuration-schema.gif)  
  
> [!CAUTION]
> Měli byste chránit konfigurační oddíly WCF v konfiguračních souborech aplikace (App. config) pomocí příslušných seznamů Access Control (ACL), aby se předešlo potenciálním bezpečnostním hrozbám.  Měli byste se třeba ujistit, že k nastavení zabezpečení pro vazby aplikací nebo v oddílu modelu služby v konfiguračním souboru pro službu mají přístup jenom odpovídající uživatelé.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [\<system.serviceModel>](system-servicemodel.md)  
 Popisuje `ServiceModel` elementu.  
  
 [\<system.serviceModel.activation>](system-servicemodel-activation.md)  
 Konfiguruje nástroj SMSvcHost. exe.  
  
 [\<system.runtime.serialization>](system-runtime-serialization.md)  
 Element nejvyšší úrovně pro nastavení možností při použití serializátorů, jako je například <xref:System.Runtime.Serialization.DataContractSerializer> .  
  
## <a name="related-sections"></a>Související oddíly  
 [Konfigurace aplikací Windows Communication Foundation](../../../wcf/configuring-services.md)  
 Popisuje postup konfigurace služeb a klientů služby WCF.
