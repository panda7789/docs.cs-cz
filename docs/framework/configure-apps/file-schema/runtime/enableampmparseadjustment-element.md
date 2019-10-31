---
title: Element <EnableAmPmParseAdjustment>
ms.date: 03/30/2017
ms.assetid: fda998a5-f538-4f8b-a18c-ee7f35e16938
ms.openlocfilehash: 8920e51fcaaca5cb78b80a99ea321163c9b5240f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73117372"
---
# <a name="enableampmparseadjustment-element"></a>\<element > EnableAmPmParseAdjustment
Určuje, zda metody analýzy data a času používají upravenou sadu pravidel k analýze datových řetězců obsahujících den, měsíc, hodinu a označení dopoledne/odpoledne.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<EnableAmPmParseAdjustment >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<EnableAmPmParseAdjustment enabled="0"|"1" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, zda metody analýzy data a času používají upravenou sadu pravidel k analýze řetězců data, které obsahují pouze označení den, měsíc, hodina a AM/PM.|  
  
### <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|0,8|Metody analýzy data a času nepoužívají upravená pravidla pro analýzu řetězců data, které obsahují pouze označení den, měsíc, hodina a AM/PM.|  
|první|Metody analýzy data a času používají upravená pravidla pro analýzu řetězců data, které obsahují pouze označení den, měsíc, hodina a AM/PM.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o možnostech inicializace modulu runtime.|  
  
## <a name="remarks"></a>Poznámky  
 Element `<EnableAmPmParseAdjustment>` řídí, jak následující metody analyzují řetězec data obsahující číselný den a měsíc následovaný hodinou a označení AM/PM (například "4/10 6 dop."):  
  
- <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTime.TryParse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTimeOffset.TryParse%2A?displayProperty=nameWithType>  
  
- <xref:System.Convert.ToDateTime%2A?displayProperty=nameWithType>  
  
 Žádné další vzory nejsou ovlivněny.  
  
 `<EnableAmPmParseAdjustment>` element nemá žádný vliv na metody <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>a <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType>.  
  
> [!IMPORTANT]
> V rozhraní .NET Core a .NET Native jsou ve výchozím nastavení povolená upravená pravidla analýzy dopoledne/odpoledne.  
  
 Pokud není pravidlo úpravy analýzy povoleno, první číslice řetězce je interpretována jako hodina 12 hodinového času a zbytek řetězce s výjimkou označení dopoledne/odpoledne je ignorován. Datum a čas vracené metodou analýzy se skládají z aktuálního data a hodiny dne extrahované z řetězce data.  
  
 Pokud je pravidlo úpravy analýzy povoleno, metoda analýzy interpretuje den a měsíc jako patřící do aktuálního roku a interpretuje čas jako hodinu z 12 hodin.  
  
 Následující tabulka ilustruje rozdíl v hodnotě <xref:System.DateTime>, pokud je metoda <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> použita k analýze řetězce "" 4/10 6 AM "s vlastností `enabled` elementu `<EnableAmPmParseAdjustment>` nastaveným na hodnotu" 0 "nebo" 1 ". Předpokládá, že dnešní datum je 5. ledna 2017 a zobrazuje datum, jako by bylo formátováno pomocí formátovacího řetězce "G" zadané jazykové verze.  
  
|Název jazykové verze|Enabled = "0"|Enabled = "1"|  
|------------------|------------------|------------------|  
|EN-US|1/5/2017 4:00:00 DOP.|4/10/2017 6:00:00 DOP.|  
|en-GB|5/1/2017 6:00:00|10/4/2017 6:00:00|  
  
## <a name="see-also"></a>Viz také:

- [\<element > runtime](runtime-element.md)
- [> element konfigurace \<](../configuration-element.md)
