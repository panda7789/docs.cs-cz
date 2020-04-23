---
title: x:FactoryMethod – direktiva
ms.date: 03/30/2017
helpviewer_keywords:
- XAML. x:FactoryMethod directive [XAML Services]
- FactoryMethod directive in XAML [XAML Services]
- x:FactoryMethod directive [XAML Services]
ms.assetid: 829bcbdf-5318-4afb-9a03-c310e0d2f23d
ms.openlocfilehash: 5e864b6f5d664b079036a5d915e2f6f81b83639f
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071533"
---
# <a name="xfactorymethod-directive"></a>x:FactoryMethod – direktiva
Určuje jinou metodu než konstruktor, kterou by měl procesor XAML použít k inicializaci objektu po vyřešení jeho typu zálohování.  
  
## <a name="xaml-attribute-usage-no-xarguments"></a>Použití atributu XAML, bez x:Argumenty  
  
```xaml  
<object x:FactoryMethod="methodname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-attribute-usage-xarguments-as-elements"></a>Použití atributu XAML, x:Argumenty jako elementy  
  
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
|`methodname`|Název metody řetězce metody, kterou procesory XAML volají k `object`inicializaci instance zadané jako . Viz Poznámky.|  
|`oneOrMoreObjectElements`|Jeden nebo více prvků objektu pro objekty, které určují parametry metody výroby. Řád je významný; označuje pořadí, ve kterém by měly být argumenty předány metodě factory.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud `methodname` je metoda instance, nelze ji kvalifikovat.  
  
 Statické metody jako metody výroby jsou podporovány. Pokud `methodname` je statická `methodname` metoda, je `typeName.methodName` k `typeName` dispozici jako kombinace, kde názvy třídy, která definuje statickou metodu factory. `typeName`může být prefix-qualified, pokud odkazuje na typ v mapovaných xmlns. `typeName`může být jiný `typeof(object)`typ než .  
  
 Metoda factory musí být deklarovanou veřejnou metodou typu, který podporuje příslušný prvek objektu.  
  
 Metoda factory musí vrátit instanci, která je přiřaditelná příslušnému objektu. Metody factory by nikdy vrátit null.  
  
 `x:Arguments`pracuje na principu nejlepší shody pro podpisy továrních metod. Odpovídající vyhodnotí počet parametrů jako první. Pokud existuje více než jedna možná shoda pro počet parametrů, je vyhodnocen typ parametru a určí se nejlepší shoda. Pokud je stále nejednoznačnost po této fázi hodnocení, chování procesoru XAML není definována.  
  
 Použití `x:FactoryMethod` prvku není použití prvku vlastnosti v typickém smyslu, protože značka směrnice neodkazuje na typ prvku obsahujícího objektu. Očekává se, že použití prvku je méně časté než použití atributu. `x:Arguments`(použití atributu nebo prvku) lze `x:FactoryMethod` použít spolu s použitím prvku, ale to není konkrétně uvedeno v části Použití.  
  
 `x:FactoryMethod`jako prvek musí předcházet jakékoli jiné prvky `x:Arguments` vlastnosti, musí předcházet všechny také k dispozici jako prvky a musí předcházet jakýkoli obsah/vnitřní text/inicializace textu.  
  
## <a name="see-also"></a>Viz také

- [x:Arguments – direktiva](xarguments-directive.md)
