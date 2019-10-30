---
title: <bindings>
ms.date: 01/22/2018
ms.assetid: b62cd369-5409-4030-8490-9759a462dd3a
ms.openlocfilehash: cd4c4cd4c1bfe7920c438eddc15aba00d995b8cb
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039623"
---
# <a name="bindings"></a>vazby \<

Pomocí elementu `bindings` můžete nakonfigurovat kolekci standardních a vlastních vazeb pro Windows Communication Foundation (WCF). Každá položka je `binding` prvek, který lze identifikovat jeho jedinečným `name`. Služby používají vazby jejich propojením pomocí `name`. Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]nejsou vazby a chování nutné mít název. Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).

## <a name="system-provided-bindings"></a>Vazby poskytované systémem

Vazby poskytované systémem skrývají složitost zasílání zpráv WCF. Aplikace využívající vazby poskytované systémem nevyžadují plnou kontrolu nad zásobníkem. Atributy vystavené pro každou vazbu poskytovanou systémem jsou ty, které jsou nejvhodnější pro scénář použití jako adresy vazby.

Konfigurační oddíl pro každou vazbu poskytovanou systémem může definovat několik konfigurací používaných ke konfiguraci vazby. Každá konfigurace je identifikována jedinečným názvem.

Nelze přidat prvky nebo atributy do vazby poskytnuté systémem. K tomu byste měli implementovat vlastní vazbu, jak je popsáno v části [vlastní vazby](#custom-bindings) . Je možné definovat vlastní vazbu, která napodobuje uživatelsky definované vazby, a přidá několik nastavení, která má uživatelská aplikace mít kontrolu nad.  

Seznam vazeb poskytovaných systémem naleznete v tématu [systémové vazby](../../../wcf/system-provided-bindings.md).

## <a name="custom-bindings"></a>Vlastní vazby

Vlastní vazby poskytují plnou kontrolu nad zásobníkem zpráv WCF. Jednotlivá vazba definuje zásobník zpráv zadáním elementů konfigurace pro prvky zásobníku v pořadí, v jakém se zobrazují v zásobníku. Každý prvek definuje a nakonfiguruje jeden prvek zásobníku. V každé vlastní vazbě musí být jeden a jenom jeden `transport` element. Bez tohoto elementu je zásobník pro zasílání zpráv neúplný.

Pořadí, ve kterém se prvky zobrazí v zásobníku, protože se jedná o pořadí, ve kterém jsou operace pro zprávu aplikovány. Požadované pořadí prvků zásobníku je následující:  

1. Transakce (volitelné)  

2. Spolehlivé zasílání zpráv (volitelné)  

3. Zabezpečení (volitelné)  

4. Kodér  

5. Přepravu  

 Vlastní vazby jsou identifikovány pomocí atributu `name`. Další informace o vlastních vazbách naleznete v tématu [Custom Bindings](../../../wcf/extending/custom-bindings.md).

## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.BindingsSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.Binding?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>
- [Vazby](../../../wcf/bindings.md)
- [Vlastní vazby](../../../wcf/extending/custom-bindings.md)
- [\<customBinding >](custombinding.md)
