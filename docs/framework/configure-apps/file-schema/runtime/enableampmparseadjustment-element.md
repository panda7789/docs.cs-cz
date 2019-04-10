---
title: <EnableAmPmParseAdjustment> Prvek
ms.date: 03/30/2017
ms.assetid: fda998a5-f538-4f8b-a18c-ee7f35e16938
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 57d1a14199debbb90827c1ea95347d485a636329
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59222507"
---
# <a name="enableampmparseadjustment-element"></a>\<EnableAmPmParseAdjustment > – Element
Určuje, zda analýzy metody data a času použít upravenou sadu pravidel k parsování řetězců kalendářních dat, které obsahují den, měsíc, hodinu a označení dopoledne/odpoledne.  
  
 \<Konfigurace >  
 \<modul runtime >  
\<EnableAmPmParseAdjustment >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<EnableAmPmParseAdjustment enabled="0"|"1" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, jestli analýzy metody data a času použít upravenou sadu pravidel k parsování řetězců kalendářních dat, které obsahují pouze den, měsíc, hodinu a označení dopoledne/odpoledne.|  
  
### <a name="enabled-attribute"></a>Atribut enabled  
  
|Value|Popis|  
|-----------|-----------------|  
|0|Datum a čas analýze metody nepoužívejte upravené pravidla pro parsování řetězců kalendářních dat, které obsahují pouze den, měsíc, hodinu a označení dopoledne/odpoledne.|  
|1|Analýzy metody data a času pomocí upravené pravidel pro parsování řetězců kalendářních dat, které obsahují pouze den, měsíc, hodinu a označení dopoledne/odpoledne.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o možnostech inicializace modulu runtime.|  
  
## <a name="remarks"></a>Poznámky  
 `<EnableAmPmParseAdjustment>` Prvek určuje, jak analyzovat řetězec data, který obsahuje číselné vyjádření dne a měsíce, za nímž následuje za hodinu a dopoledne/odpoledne (například "4/10 6 AM") v následujících metod:  
  
-   <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>  
  
-   <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>  
  
-   <xref:System.DateTime.TryParse%2A?displayProperty=nameWithType>  
  
-   <xref:System.DateTimeOffset.TryParse%2A?displayProperty=nameWithType>  
  
-   <xref:System.Convert.ToDateTime%2A?displayProperty=nameWithType>  
  
 Žádné jiné vzory jsou ovlivněny.  
  
 `<EnableAmPmParseAdjustment>` Element nemá žádný vliv <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>, a <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> metody.  
  
> [!IMPORTANT]
>  V .NET Core a .NET Native jsou ve výchozím nastavení povolené upravené pravidla analýzy dop. / odp.  
  
 Pokud není povolené analýzy pravidlo úpravy, první číslice řetězec je interpretován jako hodinu 12hodinový formát a zbytek řetězci s výjimkou dopoledne/odpoledne ignorováno. Datum a čas, vrátí metoda analýzy se skládá z aktuálního data a hodina dne z řetězce data extrahovat.  
  
 Pokud je povolené analýzy pravidlo úpravy, při analýze metody interpretovat den a měsíc jako patřící do aktuálního roku a interpretovat jako hodina 12hodinový formát času.  
  
 Následující tabulka ukazuje rozdíly <xref:System.DateTime> hodnotu v případě <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> metoda se používá pro analýzu řetězce "" 4/10 6 AM"s `<EnableAmPmParseAdjustment>` elementu `enabled` vlastnost nastavena na"0"nebo"1". Předpokládá, že dnešní datum je 5. ledna 2017 a zobrazí datum, jako kdyby je naformátována pomocí řetězec formátu "G" zadanou jazykovou verzi.  
  
|Název jazykové verze|enabled="0"|enabled="1"|  
|------------------|------------------|------------------|  
|en-US|1. 5. 2017 4:00:00: 00|4/10/2017 6:00:00: 00|  
|en-GB|5/1/2017 6:00:00|10/4/2017 6:00:00|  
  
## <a name="see-also"></a>Viz také:

- [\<modul runtime > – Element](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)
- [\<Konfigurace > – Element](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)
