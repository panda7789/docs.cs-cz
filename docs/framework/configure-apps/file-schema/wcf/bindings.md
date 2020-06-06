---
title: <bindings>
ms.date: 01/22/2018
ms.assetid: b62cd369-5409-4030-8490-9759a462dd3a
ms.openlocfilehash: fe8f620668e35183890b8bba1f254a74c962f8d3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "74139660"
---
# \<bindings>

Element lze použít `bindings` ke konfiguraci kolekce standardních a vlastní vazby pro Windows Communication Foundation (WCF). Každá položka je `binding` prvek, který lze identifikovat podle jeho jedinečného typu `name` . Služby používají vazby propojením s použitím `name` . Počínaje .NET Framework 4 nejsou vazby a chování nutné mít název. Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).

## <a name="system-provided-bindings"></a>Vazby poskytované systémem

Vazby poskytované systémem skrývají složitost zasílání zpráv WCF. Aplikace využívající vazby poskytované systémem nevyžadují plnou kontrolu nad zásobníkem. Atributy vystavené pro každou vazbu poskytovanou systémem jsou ty, které jsou nejvhodnější pro scénář použití jako adresy vazby.

Konfigurační oddíl pro každou vazbu poskytovanou systémem může definovat několik konfigurací používaných ke konfiguraci vazby. Každá konfigurace je identifikována jedinečným názvem.

Nelze přidat prvky nebo atributy do vazby poskytnuté systémem. K tomu byste měli implementovat vlastní vazbu, jak je popsáno v části [vlastní vazby](#custom-bindings) . Je možné definovat vlastní vazbu, která napodobuje uživatelsky definované vazby, a přidá několik nastavení, která má uživatelská aplikace mít kontrolu nad.  

Seznam vazeb poskytovaných systémem naleznete v tématu [systémové vazby](../../../wcf/system-provided-bindings.md).

## <a name="custom-bindings"></a>Vlastní vazby

Vlastní vazby poskytují plnou kontrolu nad zásobníkem zpráv WCF. Jednotlivá vazba definuje zásobník zpráv zadáním elementů konfigurace pro prvky zásobníku v pořadí, v jakém se zobrazují v zásobníku. Každý prvek definuje a nakonfiguruje jeden prvek zásobníku. `transport`V každé vlastní vazbě musí být pouze jeden element. Bez tohoto elementu je zásobník pro zasílání zpráv neúplný.

Pořadí, ve kterém se prvky zobrazí v zásobníku, protože se jedná o pořadí, ve kterém jsou operace pro zprávu aplikovány. Požadované pořadí prvků zásobníku je následující:  

1. Transakce (volitelné)  

2. Spolehlivé zasílání zpráv (volitelné)  

3. Zabezpečení (volitelné)  

4. Kodér  

5. Přenos  

 Vlastní vazby jsou označeny jejich `name` atributem. Další informace o vlastních vazbách naleznete v tématu [Custom Bindings](../../../wcf/extending/custom-bindings.md).

## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Configuration.BindingsSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.Binding?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>
- [Vazby](../../../wcf/bindings.md)
- [Vlastní vazby](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
