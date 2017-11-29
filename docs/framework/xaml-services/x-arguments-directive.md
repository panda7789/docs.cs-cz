---
title: "x:Arguments – direktiva"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- x:Arguments directive [XAML Services]
- Arguments directive in XAML [XAML Services]
- XAML [XAML Services], x:Arguments directive
ms.assetid: 87cc10b0-b610-4025-b6b0-ab27ca27c92e
caps.latest.revision: "12"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 00f605bba709f0ce5f3238ccc3c6ac6cd962f0a4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="xarguments-directive"></a>x:Arguments – direktiva
Argumenty vytváření balíčků pro deklaraci jiné než výchozí konstruktor objektu element v jazyce XAML, nebo na prohlášení metoda objektu factory.  
  
## <a name="xaml-element-usage-nondefault-constructor"></a>Použití elementu XAML (jiný než výchozí konstruktor)  
  
```  
<object ...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-element-usage-factory-method"></a>Použití elementu XAML (metoda factory)  
  
```  
<object x:FactoryMethod="methodName"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|`oneOrMoreObjectElements`|Jeden či více elementů objektu, které určují argumenty, které mají být předány metodě zálohování jiné než výchozí konstruktor nebo objekt pro vytváření.<br /><br /> Typická využití je použití inicializace textu v rámci objektu elementy zadat argument skutečné hodnoty. Viz část o příklady.<br /><br /> Je důležité pořadí elementů. Typy XAML v pořadí musí odpovídat typy a zadejte pořadí zálohování přetížení metody konstruktoru nebo objekt pro vytváření.|  
|`methodName`|Název metoda factory, která se má zpracovat žádné `x:Arguments` argumenty.|  
  
## <a name="dependencies"></a>Závislosti  
 `x:FactoryMethod`můžete upravit obor a chování kde `x:Arguments` platí.  
  
 Pokud žádné `x:FactoryMethod` není zadaný, `x:Arguments` se vztahuje na alternativní podpisy (jiné než výchozí) z konstruktorů zálohování.  
  
 Pokud `x:FactoryMethod` není zadaný, `x:Arguments` se vztahuje na přetížení metodu s názvem.  
  
## <a name="remarks"></a>Poznámky  
 XAML 2006 může podporovat jiné než výchozí inicializace prostřednictvím inicializace text. Praktické aplikace inicializaci text konstrukce techniky je však omezená. Inicializace textu je považován za jednoho textového řetězce; proto pouze přidá funkce pro jeden parametr inicializace pokud převaděče typu je definována pro vytváření chování, které mohou analyzovat položky vlastních informací a vlastní oddělovače z řetězce. Textový řetězec pro objekt logiky je také potenciálně převaděče typů nativní výchozí daný analyzátor jazyka XAML pro zpracování primitiv než řetězec hodnotu true.  
  
 `x:Arguments` Použití XAML není použití elementu vlastnosti v typické smysl, protože kód direktivy neodkazuje typ obsahující objekt elementu. Je třeba více podobají jiné direktivy `x:Code` kde element demarks rozsahu, ve kterém by měl být kód interpretován jako jiné než výchozí podřízené obsah. V takovém případě typ jazyka XAML jednotlivých prvků objekt komunikuje informace o typy argumentů, který je používán XAML analyzátory k určení signatury metody, které objekt pro vytváření konkrétní konstruktor `x:Arguments` využití se pokouší odkazovat.  
  
 `x:Arguments`pro element objektu musí vytvářen předcházet další vlastnosti prvky, obsah, vnitřní text nebo řetězce inicializace objektu elementu. Objekt elementů v rámci `x:Arguments` může být atributy a inicializace řetězce podle typu XAML a jeho základní metoda konstruktoru nebo objekt pro vytváření. U objektu nebo argumenty můžete zadat vlastní XAML nebo XAML typy, které jsou jinak mimo výchozí obor názvů jazyka XAML odkazem zavedených předponu mapování.  
  
 XAML procesorů pomocí následujících pokynů určete, jak jsou argumenty zadaný v `x:Arguments` se má použít k vytvoření objektu. Pokud `x:FactoryMethod` není zadaný, se porovná informace do zadané `x:FactoryMethod` (Všimněte si, že hodnota `x:FactoryMethod` je název metody, a metodu s názvem může mít přetížení. Pokud `x:FactoryMethod` není zadán, informace se porovná sadu všechny přetížení veřejný konstruktor objektu. Logika zpracování XAML pak porovná počet parametrů a vybere přetížení s odpovídající Arita. Pokud existuje více než jednu shodu, procesor XAML musí porovnat typy parametrů na základě typů XAML elementů zadaného objektu. Pokud je stále více než jednu shodu, není definován chování procesoru XAML. Pokud `x:FactoryMethod` je zadán, ale metodu nelze přeložit, procesor XAML by měla vyvolat výjimku.  
  
 Použití atributu XAML `<x:Arguments>string</x:Arguments>` je technicky možné. Však tímto způsobem žádné možnosti nad rámec co lze provést v opačném případě prostřednictvím inicializace text a typ převaděče a pomocí této syntaxe není záměr návrhu funkcí metoda factory XAML 2009.  
  
## <a name="examples"></a>Příklady  
 Následující příklad ukazuje konstruktor jiné než výchozí podpisem, pak použití XAML `x:Arguments` který přistupuje k této podpis.  
  
```csharp  
public class Food {  
    private string _name;  
    private Int32 _calories;  
    public Food(string name, Int32 calories) {  
        _name=name;  
        _calories=calories;  
    }  
}  
```  
  
```xaml  
<my:Food>  
    <x:Arguments>  
        <x:String>Apple</x:String>  
        <x:Int32>150</x:Int32>  
    </x:Arguments>  
</my:Food>  
```  
  
 Následující příklad ukazuje podpis metoda cílový objekt pro vytváření a používání XAML `x:Arguments` který přistupuje k této podpis.  
  
```csharp  
public Food TryLookupFood(string name)  
{  
  switch (name) {  
    case "Apple": return new Food("Apple",150);  
    case "Chocolate": return new Food("Chocolate",200);  
    case "Cheese": return new Food("Cheese", 450);  
    default: {return new Food(name,0);  
  }  
}  
```  
  
```xaml  
<my:Food x:FactoryMethod="TryLookupFood">  
    <x:Arguments>  
        <x:String>Apple</x:String>  
    </x:Arguments>  
</my:Food>  
```  
  
## <a name="see-also"></a>Viz také  
 [Definování vlastních typů pro použití s rozhraní .NET Framework XAML Services](../../../docs/framework/xaml-services/defining-custom-types-for-use-with-net-framework-xaml-services.md)  
 [Přehled XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
