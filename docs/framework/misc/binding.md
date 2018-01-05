---
title: '&lt;Vazba&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 666183d6-4d1f-45c7-ac64-bdf93ee8f36f
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7b9e0c7e077a9f47de6df31b00f4df320b845150
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltbindinggt"></a>&lt;Vazba&gt;
Můžete použít `binding` elementu, který chcete nakonfigurovat různé typy předdefinované vazby zadaný ve Windows Communication Foundation (WCF).  
  
## <a name="system-provided-binding"></a>Vazby poskytované systémem  
 Vazby poskytované systémem překonávají složitost systému zasílání zpráv zásobníku WCF. Aplikace, které používají vazby poskytované systémem nevyžadují plnou kontrolu nad zásobníku. Atributy zveřejněné na každé vazby poskytované systémem jsou ty, které většinu vhodné pro scénáři použití adresy vazby.  
  
 Konfigurační oddíl pro každou vazbu poskytované systémem můžete definovat několik konfigurace použít ke konfiguraci vazby. Každá konfigurace je identifikována jedinečný název.  
  
 Není možné přidat vazby poskytované systémem elementy nebo atributy. Uděláte to tak, měli byste implementovat vlastní vazby jak je popsáno v části "Vlastní vazby" v tomto tématu. Je možné definovat vlastní vazby, která napodobuje poskytované systémem vazbu perfektně a přidá několik nastavení aplikace uživatelů chce mít kontrolu nad.  
  
## <a name="custom-binding"></a>Vlastní vazba  
 Vlastní vazby poskytují plnou kontrolu nad zásobníku zasílání zpráv WCF. Jednotlivé vazby definuje zásobníku zprávu zadáním konfigurační prvky pro prvky zásobníku v pořadí, ve kterém se objeví v zásobníku. Každý prvek definuje a konfiguruje jeden element zásobníku. Musí být pouze jeden `transport` element v každé vlastní vazby. Bez tohoto elementu je nekompletní zasílání zpráv zásobníku.  
  
 Pořadí, ve kterém elementy zobrazují v zásobníku důležitý, protože je pořadí, ve kterém jsou použity operace ke zprávě. Doporučené pořadí elementů zásobníku je následující:  
  
1.  Transakce (volitelné)  
  
2.  Spolehlivé zasílání zpráv (volitelné)  
  
3.  Zabezpečení (volitelné)  
  
4.  Kodér  
  
5.  Přenos  
  
 Vlastní vazby se identifikují podle jejich `name` atribut.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.BindingsSection>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 [Vazby](../../../docs/framework/wcf/bindings.md)  
 [Vlastní vazby](../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
