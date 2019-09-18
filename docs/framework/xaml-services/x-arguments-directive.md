---
title: x:Arguments – direktiva
ms.date: 03/30/2017
helpviewer_keywords:
- x:Arguments directive [XAML Services]
- Arguments directive in XAML [XAML Services]
- XAML [XAML Services], x:Arguments directive
ms.assetid: 87cc10b0-b610-4025-b6b0-ab27ca27c92e
ms.openlocfilehash: a18de9a07839f5b01620311832b85667680c12ad
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053836"
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
|`methodName`|Název metody objektu pro vytváření, která by měla zpracovat `x:Arguments` jakékoli argumenty.|  
  
## <a name="dependencies"></a>Závislosti  
 `x:FactoryMethod`může upravit rozsah a chování, kde `x:Arguments` platí.  
  
 Pokud není zadán, `x:Arguments` platí pro alternativní (nevýchozí) podpisy záložních konstruktorů. `x:FactoryMethod`  
  
 Pokud `x:FactoryMethod` je zadáno, `x:Arguments` platí pro přetížení pojmenované metody.  
  
## <a name="remarks"></a>Poznámky  
 XAML 2006 může podporovat nevýchozí inicializaci prostřednictvím inicializačního textu. Praktické použití techniky konstrukce inicializačního textu je však omezené. Inicializační text je považován za jeden textový řetězec; Proto přidává pouze schopnost pro inicializaci jednoho parametru, pokud není definován konvertor typu pro chování konstrukce, které může analyzovat vlastní položky informací a vlastní oddělovače z řetězce. Také textový řetězec do logiky objektu je potenciálně pro zpracování primitivních primitivních typů, které jsou jiné než skutečný řetězec, zadán z nativního převaděče pro kódování XAML.  
  
 Použití `x:Arguments` jazyka XAML není použití prvku vlastností v typickém smyslu, protože označení direktivy neodkazuje na objekt obsahující typ elementu. Je více podobají na jiné direktivy, jako `x:Code` například, kde element označuje rozsah, ve kterém by měly být značky interpretovány jako jiné než výchozí pro podřízený obsah. V tomto případě typ XAML každého prvku objektu komunikuje informace o typech argumentů, které jsou používány analyzátory jazyka XAML k určení, které konkrétní konstruktory výrobní metody signatury `x:Arguments` se o použití pokouší odkazovat.  
  
 `x:Arguments`pro konstruovaný prvek objektu musí předcházet libovolné jiné prvky vlastností, obsah, vnitřní text nebo inicializační řetězce elementu Object. Prvky objektu v rámci `x:Arguments` mohou zahrnovat atributy a inicializační řetězce, jak je povoleno tímto typem XAML a jeho záložní konstruktor nebo výrobní metoda. Pro objekt nebo argumenty můžete zadat vlastní typy XAML nebo XAML, které jsou jinak mimo výchozí obor názvů XAML odkazem na zavedená mapování předpon.  
  
 Procesory XAML používají následující pokyny k určení toho, jak by měly `x:Arguments` být použity argumenty určené v pro vytvoření objektu. Je `x:FactoryMethod` -li parametr zadán, jsou informace porovnány `x:FactoryMethod` se zadaným ( `x:FactoryMethod` Všimněte si, že hodnota je název metody a pojmenovaná metoda může mít přetížení. Není `x:FactoryMethod` -li parametr zadán, jsou informace porovnány se sadou všech přetížení veřejného konstruktoru objektu. Logika zpracování XAML pak porovná počet parametrů a vybere přetížení se stejnou aritou. Pokud existuje více než jedna shoda, by měl procesor XAML porovnat typy parametrů založené na typech XAML zadaných prvků objektu. Pokud je stále více než jedna shoda, chování procesoru XAML není definováno. `x:FactoryMethod` Pokud je zadán, ale metodu nelze vyřešit, procesor XAML by měl vyvolat výjimku.  
  
 Použití `<x:Arguments>string</x:Arguments>` atributu XAML je technicky možné. To však neposkytuje žádné možnosti nad rámec toho, co by bylo možné provést jinak prostřednictvím inicializačního textu a převaděčů typů, a použití této syntaxe není záměrem návrhu funkcí rozhraní XAML 2009 pro vytváření.  
  
## <a name="examples"></a>Příklady  
 Následující příklad ukazuje signaturu konstruktoru bez parametrů, pak použití jazyka XAML pro `x:Arguments` přístup k tomuto podpisu.  
  
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
  
 Následující příklad ukazuje cílový podpis metody výroby, potom použití `x:Arguments` XAML, který přistupuje k tomuto podpisu.  
  
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
