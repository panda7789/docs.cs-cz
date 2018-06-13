---
title: '&lt;Vazby&gt;'
ms.date: 03/30/2017
ms.assetid: b62cd369-5409-4030-8490-9759a462dd3a
ms.openlocfilehash: 76ebd7c317bf5f0aa1ec02d4014235df232314f0
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747818"
---
# <a name="ltbindingsgt"></a>&lt;Vazby&gt;
Tato část obsahuje kolekci standardní a vlastní vazby. Každá položka je `binding` element, který lze identifikovat podle jeho jedinečné `name`. Služby používají vazby jejich propojováním pomocí `name`. Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název. Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="system-provided-binding"></a>Vazby poskytované systémem  
 Vazby poskytované systémem překonávají složitost systému zasílání zpráv zásobníku WCF. Aplikace, které používají vazby poskytované systémem nevyžadují plnou kontrolu nad zásobníku. Atributy zveřejněné na každé vazby poskytované systémem jsou ty, které většinu vhodné pro scénáři použití adresy vazby.  
  
 Konfigurační oddíl pro každou vazbu poskytované systémem můžete definovat několik konfigurace použít ke konfiguraci vazby. Každá konfigurace je identifikována jedinečný název.  
  
 Není možné přidat vazby poskytované systémem elementy nebo atributy. Uděláte to tak, měli byste implementovat vlastní vazby jak je popsáno v části "Vlastní vazby" v tomto tématu. Je možné definovat vlastní vazby, která napodobuje poskytované systémem vazbu perfektně a přidá několik nastavení aplikace uživatelů chce mít kontrolu nad.  
  
 Seznam vazeb poskytovaných systémem najdete v tématu [System-Provided vazby](../../../../../docs/framework/wcf/system-provided-bindings.md).  
  
## <a name="custom-binding"></a>Vlastní vazba  
 Vlastní vazby poskytují plnou kontrolu nad zásobníku zasílání zpráv WCF. Jednotlivé vazby definuje zásobníku zprávu zadáním konfigurační prvky pro prvky zásobníku v pořadí, ve kterém se objeví v zásobníku. Každý prvek definuje a konfiguruje jeden element zásobníku. Musí být pouze jeden `transport` element v každé vlastní vazby. Bez tohoto elementu je nekompletní zasílání zpráv zásobníku.  
  
 Pořadí, ve kterém elementy zobrazují v zásobníku důležitý, protože je pořadí, ve kterém jsou použity operace ke zprávě. Požadované pořadí prvků zásobníku je následující:  
  
1.  Transakce (volitelné)  
  
2.  Spolehlivé zasílání zpráv (volitelné)  
  
3.  Zabezpečení (volitelné)  
  
4.  Kodér  
  
5.  Přenos  
  
 Vlastní vazby se identifikují podle jejich `name` atribut. Další informace o vlastních vazeb naleznete v tématu [vlastní vazby](../../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.BindingsSection>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Vlastní vazby](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [\<Vazba >](../../../../../docs/framework/misc/binding.md)
