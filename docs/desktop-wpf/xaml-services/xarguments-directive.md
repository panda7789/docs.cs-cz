---
title: x:Arguments – direktiva
ms.date: 03/30/2017
helpviewer_keywords:
- x:Arguments directive [XAML Services]
- Arguments directive in XAML [XAML Services]
- XAML [XAML Services], x:Arguments directive
ms.assetid: 87cc10b0-b610-4025-b6b0-ab27ca27c92e
ms.openlocfilehash: 5ec6e192688e1065ea847db6c175ad9da0e743fe
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071589"
---
# <a name="xarguments-directive"></a>x:Arguments – direktiva

Balíčky argumenty konstrukce pro deklaraci objektu objektu konstruktoru bez parametrů v XAML nebo pro deklaraci objektu metody factory.

## <a name="xaml-element-usage-nonparameterless-constructor"></a>Využití prvků XAML (konstruktor bez parametrů)

```xaml
<object ...>
  <x:Arguments>
    oneOrMoreObjectElements
  </x:Arguments>
</object>
```

## <a name="xaml-element-usage-factory-method"></a>Použití prvku XAML (tovární metoda)

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
|`oneOrMoreObjectElements`|Jeden nebo více prvků objektu, které určují argumenty, které mají být předány záložnímu konstruktoru nebo metodě výroby bez parametrů.<br /><br /> Typické použití je použití inicializačního textu v rámci prvků objektu k určení skutečných hodnot argumentů. Viz příklady oddílu.<br /><br /> Pořadí prvků je významné. XAML typy v pořadí musí odpovídat typy a pořadí typů záložní konstruktor nebo přetížení metody výroby.|
|`methodName`|Název metody factory, která by `x:Arguments` měla zpracovat všechny argumenty.|

## <a name="dependencies"></a>Závislosti

`x:FactoryMethod`můžete upravit rozsah a `x:Arguments` chování, kde platí.

Pokud `x:FactoryMethod` není zadán, `x:Arguments` platí pro alternativní (nevýchozí) podpisy záložních konstruktorů.

Pokud `x:FactoryMethod` je `x:Arguments` zadán, platí pro přetížení pojmenované metody.

## <a name="remarks"></a>Poznámky

XAML 2006 může podporovat nevýchozí inicializaci prostřednictvím inicializačního textu. Praktická aplikace techniky konstrukce inicializace textu je však omezená. Inicializační text je považován za jeden textový řetězec; Proto pouze přidá schopnost pro jeden parametr inicializace, pokud převaděč typu je definován pro chování konstrukce, která může analyzovat vlastní informace položky a vlastní oddělovače z řetězce. Také textový řetězec na objekt logiky je potenciálně dané XAML analyzátor nativní výchozí typ převaděč pro zpracování primitiv jiných než true řetězec.

Použití `x:Arguments` XAML není použití prvku vlastnosti v typickém smyslu, protože značka směrnice neodkazuje na typ prvku obsahujícího objektu. Je více podobné jiné direktivy, jako je například `x:Code` kde prvek označuje rozsah, ve kterém by měl být interpretován jako jiné než výchozí pro podřízený obsah. V tomto případě xaml typ každého prvku objektu sděluje informace o typech argumentů, které používají analyzátory XAML k určení, který konkrétní podpis metody výroby konstruktoru `x:Arguments` se pokouší odkazovat.

`x:Arguments`pro prvek objektu, který je vytvářen, musí předcházet všem ostatním prvkům vlastností, obsahu, vnitřnímu textu nebo inicializačním řetězcům prvku objektu. Objektové prvky v rámci `x:Arguments` mohou obsahovat atributy a inicializační řetězce, jak to povoluje daný typ XAML a jeho záložní konstruktor nebo metoda výroby. Pro objekt nebo argumenty můžete zadat vlastní typy XAML nebo typy XAML, které jsou jinak mimo výchozí obor názvů XAML odkazem na vytvořené mapování předpony.

XAML procesory použít následující pokyny k určení, `x:Arguments` jak argumenty zadané v má být použit k vytvoření objektu. Pokud `x:FactoryMethod` je zadán, informace je `x:FactoryMethod` porovnán se zadaným (všimněte si, že hodnota `x:FactoryMethod` je název metody a pojmenovaná metoda může mít přetížení. Pokud `x:FactoryMethod` není zadán, informace je porovnán se sadou všech přetížení veřejné konstruktoru objektu. Logika zpracování XAML pak porovná počet parametrů a vybere přetížení s odpovídající arity. Pokud existuje více než jedna shoda, procesor XAML by měl porovnat typy parametrů na základě typů XAML zadaných prvků objektu. Pokud je stále více než jedna shoda, chování procesoru XAML není definována. Pokud `x:FactoryMethod` a je zadán, ale metoda nemůže být vyřešena, procesor XAML by měl vyvolat výjimku.

Použití atributu `<x:Arguments>string</x:Arguments>` XAML je technicky možné. To však poskytuje žádné možnosti nad rámec toho, co by bylo možné provést jinak prostřednictvím převaděčů inicializace textu a typu a pomocí této syntaxe není záměr návrhu funkce metody výroby XAML 2009.

## <a name="examples"></a>Příklady

Následující příklad ukazuje podpis konstruktoru bez parametrů, pak xaml použití tohoto přístupu `x:Arguments` k tomuto podpisu.

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

Následující příklad ukazuje podpis cílové metody výroby, pak `x:Arguments` xaml použití, které přistupuje k tomuto podpisu.

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

- [Definování vlastních typů pro použití s .NET XAML Services](define-custom-types.md)
- [Přehled XAML (WPF)](../fundamentals/xaml.md)
