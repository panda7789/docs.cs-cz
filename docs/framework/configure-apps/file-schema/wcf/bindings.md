---
title: <bindings>
ms.date: 01/22/2018
ms.assetid: b62cd369-5409-4030-8490-9759a462dd3a
ms.openlocfilehash: 1292bc38ce1e542086edac5539c1b29e619e2a32
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926383"
---
# <a name="bindings"></a>\<> vazeb

`bindings` Element lze použít ke konfiguraci kolekce standardních a vlastní vazby pro Windows Communication Foundation (WCF). Každá položka je prvek `binding` , který lze identifikovat podle jeho jedinečného `name`typu. Služby používají vazby propojením s použitím `name`. [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]Od, není nutné, aby vazby a chování měly název. Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="system-provided-bindings"></a>Vazby poskytované systémem
 
 Vazby poskytované systémem skrývají složitost zasílání zpráv WCF. Aplikace využívající vazby poskytované systémem nevyžadují plnou kontrolu nad zásobníkem. Atributy vystavené pro každou vazbu poskytovanou systémem jsou ty, které jsou nejvhodnější pro scénář použití jako adresy vazby.  
  
 Konfigurační oddíl pro každou vazbu poskytovanou systémem může definovat několik konfigurací používaných ke konfiguraci vazby. Každá konfigurace je identifikována jedinečným názvem.  
  
 Nelze přidat prvky nebo atributy do vazby poskytnuté systémem. K tomu byste měli implementovat vlastní vazbu, jak je popsáno v části [vlastní vazby](#custom-bindings) . Je možné definovat vlastní vazbu, která napodobuje uživatelsky definované vazby, a přidá několik nastavení, která má uživatelská aplikace mít kontrolu nad.  
  
 Seznam vazeb poskytovaných systémem naleznete v tématu [systémové vazby](../../../wcf/system-provided-bindings.md).  
  
## <a name="custom-bindings"></a>Vlastní vazby

 Vlastní vazby poskytují plnou kontrolu nad zásobníkem zpráv WCF. Jednotlivá vazba definuje zásobník zpráv zadáním elementů konfigurace pro prvky zásobníku v pořadí, v jakém se zobrazují v zásobníku. Každý prvek definuje a nakonfiguruje jeden prvek zásobníku. V každé vlastní vazbě musí být `transport` pouze jeden element. Bez tohoto elementu je zásobník pro zasílání zpráv neúplný.  
  
 Pořadí, ve kterém se prvky zobrazí v zásobníku, protože se jedná o pořadí, ve kterém jsou operace pro zprávu aplikovány. Požadované pořadí prvků zásobníku je následující:  
  
1. Transakce (volitelné)  
  
2. Spolehlivé zasílání zpráv (volitelné)  
  
3. Zabezpečení (volitelné)  
  
4. Kodér  
  
5. Přepravu  
  
 Vlastní vazby jsou označeny jejich `name` atributem. Další informace o vlastních vazbách naleznete v tématu [Custom Bindings](../../../wcf/extending/custom-bindings.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.BindingsSection?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.Binding?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>  
- [Vazby](../../../wcf/bindings.md)  
- [Vlastní vazby](../../../wcf/extending/custom-bindings.md)  
- [\<customBinding>](custombinding.md)  
- [\<> vazby](../../../misc/binding.md)
