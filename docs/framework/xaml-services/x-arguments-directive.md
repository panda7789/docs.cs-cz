---
title: x:Arguments – direktiva
ms.date: 03/30/2017
helpviewer_keywords:
- x:Arguments directive [XAML Services]
- Arguments directive in XAML [XAML Services]
- XAML [XAML Services], x:Arguments directive
ms.assetid: 87cc10b0-b610-4025-b6b0-ab27ca27c92e
ms.openlocfilehash: a87542513ffeeec7efc526d4218f921d1b7579a1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61953956"
---
# <a name="xarguments-directive"></a>x:Arguments – direktiva
Argumenty vytváření balíčků pro deklaraci jiného než výchozího konstruktoru objektu prvku v XAML nebo pro deklaraci objektu factory metody.  
  
## <a name="xaml-element-usage-nondefault-constructor"></a>Použití elementu XAML (jiný než výchozí konstruktor)  
  
```  
<object ...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-element-usage-factory-method"></a>Použití elementu XAML (výrobní metoda)  
  
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
|`oneOrMoreObjectElements`|Jeden nebo více elementů objektu, které určují argumenty, které mají být předány jiné než výchozí konstruktor nebo výrobní metoda zálohování.<br /><br /> Typické použití je použití inicializace textu v rámci elementů objektu určit skutečný argument hodnoty. Viz část o příklady.<br /><br /> Je důležité pořadí prvků. Typy XAML v pořadí musí odpovídají typům a zadejte pořadí přetížení základní konstruktor nebo výrobní metoda.|  
|`methodName`|Název metoda factory, který by měl zpracovat žádné `x:Arguments` argumenty.|  
  
## <a name="dependencies"></a>Závislosti  
 `x:FactoryMethod` můžete upravit rozsah a chování kde `x:Arguments` platí.  
  
 Pokud ne `x:FactoryMethod` není zadána, `x:Arguments` se vztahuje na alternativní podpisy (jiné než výchozí) Základní konstruktory.  
  
 Pokud `x:FactoryMethod` není zadána, `x:Arguments` platí pro přetíženou metodu s názvem.  
  
## <a name="remarks"></a>Poznámky  
 XAML 2006 můžete podporovat jiné než výchozí inicializace prostřednictvím inicializace text. Praktické aplikace inicializaci text konstrukce postup je však omezená. Inicializace text je považován za jeden řetězec textu; proto pouze přidá funkce pro inicializaci jediný parametr Pokud je definován konvertor typu pro konstrukce chování, které mohou analyzovat položky vlastních informací a vlastních oddělovačů z řetězce. Textový řetězec do objektu logiky je také potenciálně daný analyzátor XAML nativní výchozí konvertor typu pro zpracování primitivních elementů než řetězce true.  
  
 `x:Arguments` Využití XAML není použití elementu vlastnosti v typické smysl, protože direktiv značek neodkazuje na typ obsahující objekt elementu. Je třeba více podobají jiné direktivy `x:Code` kde element demarks rozsahu, ve kterém kód by měl být interpretován jako jiné než výchozí hodnota pro podřízený obsah. V takovém případě komunikuje se informace o typů argumentů, které analyzátory XAML používají k určení signatury metody, které objekt pro vytváření konkrétního konstruktoru typu každého prvku objektu XAML `x:Arguments` využití se pokouší odkazovat.  
  
 `x:Arguments` pro element objektu při konstrukci musí předcházet před všechny ostatní elementy vlastnosti, obsah, vnitřní text nebo inicializace řetězce elementu objektu. Elementů objektu v rámci `x:Arguments` mohou obsahovat atributy a inicializace řetězce, jak je od typu XAML a jeho základní konstruktor nebo výrobní metoda. Pro objekt nebo argumenty můžete zadat vlastní typy XAML nebo XAML, které jsou jinak mimo výchozí obor názvů XAML pomocí odkazu na zavedených předponu mapování.  
  
 XAML procesorů použijte následující pokyny k určení, jak jsou argumenty zadané v `x:Arguments` by měla sloužit k vytvoření objektu. Pokud `x:FactoryMethod` není zadán, bude porovnána informace do zadaného `x:FactoryMethod` (Všimněte si, že hodnota `x:FactoryMethod` je název metody, a metodu s názvem může mít přetížení. Pokud `x:FactoryMethod` není zadán, informace se porovnává se sadu všechna přetížení veřejný konstruktor objektu. Logika zpracování XAML poté porovnává počet parametrů a vybere přetížení s odpovídající Arita. Pokud existuje více než jedna shoda, by měl procesoru XAML porovnat typy parametrů na základě typů XAML prvky zadaného objektu. Pokud je stále více než jedna shoda, XAML procesoru chování není definováno. Pokud `x:FactoryMethod` je zadán, ale metoda nemůže být vyřešen, procesor XAML by měla vyvolat výjimku.  
  
 Použití atributu XAML `<x:Arguments>string</x:Arguments>` je technicky možný. Však získáte žádné možnosti nad rámec běžné co může udělat jinak inicializace text a typ převaděče a pomocí této syntaxe není záměr návrh funkce XAML 2009 objekt pro vytváření metody.  
  
## <a name="examples"></a>Příklady  
 Následující příklad ukazuje jiného než výchozího konstruktoru podpis a poté využití XAML `x:Arguments` , který přistupuje k podpisu.  
  
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
  
 Následující příklad ukazuje podpis metody cílový objekt pro vytváření a používání XAML `x:Arguments` , který přistupuje k podpisu.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Definování vlastních typů pro práci s technologií .NET Framework XAML Services](defining-custom-types-for-use-with-net-framework-xaml-services.md)
- [Přehled XAML (WPF)](../wpf/advanced/xaml-overview-wpf.md)
