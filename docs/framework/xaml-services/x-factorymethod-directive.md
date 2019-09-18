---
title: x:FactoryMethod – direktiva
ms.date: 03/30/2017
helpviewer_keywords:
- XAML. x:FactoryMethod directive [XAML Services]
- FactoryMethod directive in XAML [XAML Services]
- x:FactoryMethod directive [XAML Services]
ms.assetid: 829bcbdf-5318-4afb-9a03-c310e0d2f23d
ms.openlocfilehash: 586965dd4094e81fd830a09b64604cf33f195630
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053778"
---
# <a name="xfactorymethod-directive"></a>x:FactoryMethod – direktiva
Určuje metodu jinou než konstruktor, který by měl procesor XAML použít k inicializaci objektu po vyřešení jeho typu zálohování.  
  
## <a name="xaml-attribute-usage-no-xarguments"></a>Použití atributu XAML bez X:Arguments –  
  
```xaml  
<object x:FactoryMethod="methodname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-attribute-usage-xarguments-as-elements"></a>Použití atributu XAML, X:arguments – jako element (y)  
  
```xaml  
<object x:FactoryMethod="methodname"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|`methodname`|Řetězcová metoda názvu metody, kterou volají procesory XAML pro inicializaci instance určené jako `object`. Viz poznámky.|  
|`oneOrMoreObjectElements`|Jeden nebo více prvků objektu pro objekty, které určují parametry metody továrního nastavení. Pořadí je důležité. označuje pořadí, ve kterém by měly být argumenty předány metodě pro vytváření.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud `methodname` je metoda instance, nemůže být kvalifikována.  
  
 Jsou podporovány statické metody jako metody výroby. Pokud `methodname` je statická metoda, `methodname` je k dispozici jako *TypeName*. *methodName* kombinace, kde *TypeName* jmenuje třídu, která definuje statickou metodu Factory. *TypeName* může být kvalifikována předpona, pokud se odkazuje na typ v mapované xmlns. *TypeName* může být jiný typ než `typeof(object)`.  
  
 Metoda factory musí být deklarovanou veřejnou metodou typu, který zálohuje příslušný prvek objektu.  
  
 Metoda factory musí vracet instanci, kterou lze přiřadit příslušnému objektu. Metody továrny by nikdy neměly vracet hodnotu null.  
  
 `x:Arguments`funguje na principu nejlepší shody pro signatury metod výroby. Při shodě se vyhodnocuje počet parametrů jako první. Pokud existuje více než jedna možná shoda pro počet parametrů, je pak vyhodnocen typ parametru a je určena nejlepší shoda. Pokud je po této fázi vyhodnocení stále nejednoznačnost, chování procesoru XAML není definováno.  
  
 Použití `x:FactoryMethod` prvku není využití prvku vlastností v typickém smyslu, protože označení direktivy neodkazuje na objekt obsahující typ elementu. Je očekáváno, že použití prvku je méně běžné než použití atributu. `x:Arguments`(buď atribut nebo použití elementu) lze použít společně s `x:FactoryMethod` použitím elementu, ale to není výslovně uvedeno v oddílech použití.  
  
 `x:FactoryMethod`prvek musí předcházet všem ostatním prvkům vlastností, musí předcházet `x:Arguments` také jako element a musí předcházet jakémukoli obsahu, vnitřní text nebo inicializační text.  
  
## <a name="see-also"></a>Viz také:

- [x:Arguments – direktiva](x-arguments-directive.md)
