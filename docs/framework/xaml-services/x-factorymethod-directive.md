---
title: "x:FactoryMethod – direktiva"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML. x:FactoryMethod directive [XAML Services]
- FactoryMethod directive in XAML [XAML Services]
- x:FactoryMethod directive [XAML Services]
ms.assetid: 829bcbdf-5318-4afb-9a03-c310e0d2f23d
caps.latest.revision: "8"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 58349c5440d0062c64346933e48b64de6c4c7b60
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="xfactorymethod-directive"></a>x:FactoryMethod – direktiva
Určuje metodu než konstruktor, který se inicializovat objekt po vyřešení jeho základní typ měli použít procesor XAML.  
  
## <a name="xaml-attribute-usage-no-xarguments"></a>Použití atributu XAML, x: Arguments  
  
```  
<object x:FactoryMethod="methodname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-attribute-usage-xarguments-as-elements"></a>Použití atributu XAML, x: Arguments jako elementy  
  
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
|`methodname`|Název metody řetězec metody, která XAML procesory volání k inicializaci instance zadaný jako `object`. V části poznámky.|  
|`oneOrMoreObjectElements`|Jeden či více elementů objektu pro objekty, které určují parametry metody objektu pro vytváření. Pořadí je důležité. Označuje, pořadí, ve kterém by měla být předána argumenty metoda objektu factory.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud `methodname` je metoda instance, nemůže být kvalifikovaný.  
  
 Statické metody jako objekt pro vytváření metody jsou podporovány. Pokud `methodname` je statickou metodu `methodname` je k dispozici jako *typeName*. *methodName* kombinací, kde *typeName* názvy třídy, která definuje metoda statické objektu factory. *typeName* může být předponou kvalifikovaný Pokud odkazující k typu v namapované xmlns. *typeName* může být jiného typu než `typeof(``object``)`.  
  
 Metoda factory musí být deklarovaný veřejná metoda typu, který zálohuje relevantní objekt elementu.  
  
 Metoda factory musí vrátit instanci, která je přiřadit k příslušný objekt. Metodami pro vytváření, nikdy by měl vrátit hodnotu null.  
  
 `x:Arguments`funguje na princip nejlepší shodu pro podpis metody objektu pro vytváření. Odpovídající nejprve vyhodnotí počet parametrů. Pokud existuje více než jeden možný odpovídající počet parametrů, je typ parametru se určuje vyhodnotí a nejlepší shodu. Pokud je stále nejednoznačnosti po této fáze hodnocení, XAML procesoru chování není definován.  
  
 `x:FactoryMethod` Použití elementu není použití elementu vlastnosti v typické smysl, protože kód direktivy neodkazuje typ obsahující objekt elementu. Očekává se použití tohoto elementu je méně častých než použití atributu. `x:Arguments`(použití atributu nebo elementu) můžete použít společně s `x:FactoryMethod` použití elementu, ale to není konkrétně uvedené v částech využití.  
  
 `x:FactoryMethod`jako element musí předcházet další prvky vlastnost, musí předcházet žádné `x:Arguments` také k dispozici jako elementy a musí předcházet jakýkoli text obsahu nebo vnitřní text/inicializace.  
  
## <a name="see-also"></a>Viz také  
 [x:Arguments – direktiva](../../../docs/framework/xaml-services/x-arguments-directive.md)
