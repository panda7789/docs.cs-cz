---
title: x:FactoryMethod – direktiva
ms.date: 03/30/2017
helpviewer_keywords:
- XAML. x:FactoryMethod directive [XAML Services]
- FactoryMethod directive in XAML [XAML Services]
- x:FactoryMethod directive [XAML Services]
ms.assetid: 829bcbdf-5318-4afb-9a03-c310e0d2f23d
ms.openlocfilehash: 436caa9b93467dcf2a0763bcc0962a2beb722315
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2018
ms.locfileid: "46699193"
---
# <a name="xfactorymethod-directive"></a>x:FactoryMethod – direktiva
Určuje jiné metody než konstruktor, který procesor XAML by měla použít pro inicializaci objektu po vyřešení jeho základní typ.  
  
## <a name="xaml-attribute-usage-no-xarguments"></a>Použití atributu XAML, x: Arguments  
  
```  
<object x:FactoryMethod="methodname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-attribute-usage-xarguments-as-elements"></a>Použití atributu XAML, x: Arguments jako jeden či více elementů  
  
```  
<object x:FactoryMethod="methodname"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|`methodname`|Název metody řetězec metody, která XAML procesory volání za účelem inicializace určenou jako instanci `object`. Viz poznámky.|  
|`oneOrMoreObjectElements`|Jeden nebo více elementů objektu pro objekty, které určují parametry metody objekt pro vytváření. Pořadí je důležité. To znamená pořadí, ve kterém by měly být předány argumenty výrobní metoda.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud `methodname` je metoda instance, nemůže být kvalifikovaný.  
  
 Statické metody jako metody pro vytváření objektů jsou podporovány. Pokud `methodname` je statická metoda `methodname` se poskytuje jako *typeName*. *methodName* kombinaci, kde *typeName* názvy třídy, která definuje statické výrobní metoda. *typeName* může být předponou kvalifikací odkazující k typu v mapovaných xmlns. *typeName* může být jiného typu než `typeof(object)`.  
  
 Metoda factory musí být deklarované veřejnou metodu typu, který zálohuje elementu příslušný objekt.  
  
 Výrobní metoda musí vracet instanci, která je přiřadit k příslušný objekt. Metody pro vytváření objektů by nikdy vrátit hodnotu null.  
  
 `x:Arguments` funguje na principu nejlepší shodu pro podpis metody pro vytváření objektů. Odpovídající nejprve vyhodnotí počet parametrů. Pokud existuje více než jednu možnou shodu počet parametrů, je typ parametru je určena Vyhodnocená a nejlepší shoda. Pokud po této fáze hodnocení stále existuje nejednoznačnost, XAML procesoru chování není definováno.  
  
 `x:FactoryMethod` Použití elementu není použití elementu vlastnosti v typické smysl, protože direktiv značek neodkazuje na typ obsahující objekt elementu. Očekává se, že použití elementu je méně častý než použití atributu. `x:Arguments` (použití atributu nebo elementu) lze použít společně s `x:FactoryMethod` použití elementu, ale to není konkrétně zobrazený v částech využití.  
  
 `x:FactoryMethod` jak elementu musí předcházet před jinými prvky, vlastnost, musí předcházet všechny `x:Arguments` také ve formě elementy a musí předcházet text obsahu/vnitřní text/inicializace.  
  
## <a name="see-also"></a>Viz také  
 [x:Arguments – direktiva](../../../docs/framework/xaml-services/x-arguments-directive.md)
