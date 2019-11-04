---
title: x:Arguments – direktiva
ms.date: 03/30/2017
helpviewer_keywords:
- x:Arguments directive [XAML Services]
- Arguments directive in XAML [XAML Services]
- XAML [XAML Services], x:Arguments directive
ms.assetid: 87cc10b0-b610-4025-b6b0-ab27ca27c92e
ms.openlocfilehash: 338286b417c78b7cceeb30188e888928a15607cd
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458651"
---
# <a name="xarguments-directive"></a>x:Arguments – direktiva
Argumenty konstrukce balíčků pro deklaraci elementu objektu konstruktoru bez parametrů v jazyce XAML nebo pro deklaraci objektu metody Factory.  
  
## <a name="xaml-element-usage-nonparameterless-constructor"></a>Použití prvku XAML (konstruktor bez parametrů)  
  
```xaml  
<object ...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-element-usage-factory-method"></a>Použití elementu XAML (metoda Factory)  
  
```xaml  
<object x:FactoryMethod="methodName"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|`oneOrMoreObjectElements`|Jeden nebo více prvků objektu, které určují argumenty, které mají být předány do back-konstruktoru bez parametrů nebo metody Factory.<br /><br /> Typické použití je použití inicializačního textu v rámci prvků objektu k určení skutečných hodnot argumentů. Viz část příklady.<br /><br /> Pořadí prvků je významné. Typy XAML v pořadí musí odpovídat typům a pořadím typu konstruktoru zálohování nebo přetížení metody výroby.|  
|`methodName`|Název metody objektu pro vytváření, která by měla zpracovat jakékoli argumenty `x:Arguments`.|  
  
## <a name="dependencies"></a>Závislosti  
 `x:FactoryMethod` může upravit rozsah a chování, kde se `x:Arguments` vztahuje.  
  
 Pokud není zadán žádný `x:FactoryMethod`, `x:Arguments` se vztahuje na alternativní (nevýchozí) podpisy záložních konstruktorů.  
  
 Je-li zadán `x:FactoryMethod`, `x:Arguments` se vztahuje na přetížení pojmenované metody.  
  
## <a name="remarks"></a>Poznámky  
 XAML 2006 může podporovat nevýchozí inicializaci prostřednictvím inicializačního textu. Praktické použití techniky konstrukce inicializačního textu je však omezené. Inicializační text je považován za jeden textový řetězec; Proto přidává pouze schopnost pro inicializaci jednoho parametru, pokud není definován konvertor typu pro chování konstrukce, které může analyzovat vlastní položky informací a vlastní oddělovače z řetězce. Také textový řetězec do logiky objektu je potenciálně pro zpracování primitivních primitivních typů, které jsou jiné než skutečný řetězec, zadán z nativního převaděče pro kódování XAML.  
  
 Použití `x:Arguments` XAML není využití prvku vlastností v typickém smyslu, protože označení direktivy neodkazuje na objekt obsahující typ elementu. Je více podobají na jiné direktivy, jako například `x:Code`, kde element označuje rozsah, ve kterém by měly být značky interpretovány jako jiné než výchozí pro podřízený obsah. V tomto případě typ XAML každého prvku objektu komunikuje informace o typech argumentů, které jsou používány analyzátory jazyka XAML k určení konkrétního typu signatury výrobní metody, `x:Arguments` se pokouší o odkazování.  
  
 `x:Arguments` pro konstruovaný prvek objektu musí předcházet všem ostatním prvkům vlastností, obsahu, vnitřnímu textu nebo inicializačním řetězcům elementu Object. Prvky objektu v rámci `x:Arguments` mohou zahrnovat atributy a inicializační řetězce, jak jsou povoleny tímto typem XAML a jeho záložním konstruktorem nebo výrobní metodou. Pro objekt nebo argumenty můžete zadat vlastní typy XAML nebo XAML, které jsou jinak mimo výchozí obor názvů XAML odkazem na zavedená mapování předpon.  
  
 Procesory XAML používají následující pokyny k určení toho, jak by měly být použity argumenty určené v `x:Arguments` k vytvoření objektu. Je-li zadán `x:FactoryMethod`, jsou informace porovnány se zadaným `x:FactoryMethod` (Všimněte si, že hodnota `x:FactoryMethod` je název metody a pojmenovaná metoda může mít přetížení. Pokud není zadán `x:FactoryMethod`, jsou informace porovnány se sadou všech přetížení veřejného konstruktoru objektu. Logika zpracování XAML pak porovná počet parametrů a vybere přetížení se stejnou aritou. Pokud existuje více než jedna shoda, by měl procesor XAML porovnat typy parametrů založené na typech XAML zadaných prvků objektu. Pokud je stále více než jedna shoda, chování procesoru XAML není definováno. Pokud je zadána `x:FactoryMethod`, ale metodu nelze vyřešit, procesor XAML by měl vyvolat výjimku.  
  
 `<x:Arguments>string</x:Arguments>` využití atributů XAML je technicky možné. To však neposkytuje žádné možnosti nad rámec toho, co by bylo možné provést jinak prostřednictvím inicializačního textu a převaděčů typů, a použití této syntaxe není záměrem návrhu funkcí rozhraní XAML 2009 pro vytváření.  
  
## <a name="examples"></a>Příklady  
 Následující příklad ukazuje signaturu konstruktoru bez parametrů, pak použití `x:Arguments` jazyka XAML, které přistupuje k tomuto podpisu.  
  
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
  
 Následující příklad ukazuje cílový podpis metody objektu factory a pak použití jazyka XAML `x:Arguments`, který tento podpis přistupuje.  
  
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
- [Přehled XAML (WPF)](../../desktop-wpf/fundamentals/xaml.md)
