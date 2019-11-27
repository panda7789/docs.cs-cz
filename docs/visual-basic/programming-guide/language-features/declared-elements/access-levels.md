---
title: Úrovně přístupu
ms.date: 05/10/2018
helpviewer_keywords:
- members [Visual Basic], accessing in Visual Basic
- Friend access modifier
- access levels, declared elements
- access levels
- access modifiers
- Public access modifier
- Protected access modifier
- Protected Friend access modifier
- Private Protected access modifier
- Private access modifier
- declared elements [Visual Basic], access level
ms.assetid: 6e06c1ab-fd78-47f0-83a8-1152780b5e1a
ms.openlocfilehash: 33a218a2acc3c876428d6c9a887280a559f84323
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348683"
---
# <a name="access-levels-in-visual-basic"></a>Úrovně přístupu v jazyce Visual Basic

*Úroveň přístupu* deklarovaného prvku je rozsah možností přístupu, to znamená, jaký kód má oprávnění ke čtení nebo zápisu do něj. Tato funkce je určena nejen pomocí způsobu, jakým deklarujete samotný prvek, ale také úrovní přístupu kontejneru elementu. Kód, který nemůže přistupovat k nadřazenému prvku, nemůže získat přístup k žádnému z obsažených prvků, i když jsou deklarovány jako `Public`. Například `Public`ová proměnná ve `Private` struktuře je k dispozici v rámci třídy, která obsahuje strukturu, ale nikoli z vnějšku této třídy.

## <a name="public"></a>Public

Klíčové slovo [Public](../../../language-reference/modifiers/public.md) v příkazu Declaration určuje, že lze k elementu přejít z kódu kdekoli ve stejném projektu, z jiných projektů, které odkazují na projekt a ze všech sestavení sestavených z projektu. Následující kód ukazuje ukázkovou `Public`ovou deklaraci:

```vb
Public Class ClassForEverybody
```

`Public` lze použít pouze na úrovni modulu, rozhraní nebo oboru názvů. To znamená, že můžete deklarovat veřejný prvek na úrovni zdrojového souboru nebo oboru názvů nebo uvnitř rozhraní, modulu, třídy nebo struktury, ale ne v proceduře.
  
## <a name="protected"></a>Chráněno

Klíčové slovo [Protected](../../../language-reference/modifiers/protected.md) v příkazu Declaration určuje, že element lze použít pouze v rámci stejné třídy nebo z třídy odvozené z této třídy. Následující kód ukazuje ukázkovou `Protected`ovou deklaraci:

```vb
Protected Class ClassForMyHeirs
```

`Protected` lze použít pouze na úrovni třídy a pouze v případě, že deklarujete člena třídy. To znamená, že můžete deklarovat chráněný element ve třídě, ale ne na úrovni zdrojového souboru nebo oboru názvů, nebo uvnitř rozhraní, modulu, struktury nebo procedury.

## <a name="friend"></a>Friend

Klíčové slovo [Friend](../../../language-reference/modifiers/friend.md) v příkazu Declaration určuje, že k elementu lze přistupovat ze stejného sestavení, ale nikoli z vnějšku sestavení. Následující kód ukazuje ukázkovou `Friend`ovou deklaraci:

```vb
Friend stringForThisProject As String
```

`Friend` lze použít pouze na úrovni modulu, rozhraní nebo oboru názvů. To znamená, že můžete deklarovat element Friend na úrovni zdrojového souboru nebo oboru názvů, nebo uvnitř rozhraní, modulu, třídy nebo struktury, ale ne v proceduře.

## <a name="protected-friend"></a>Protected Friend

Kombinace klíčového slova [Protected Friend](../../../language-reference/modifiers/protected-friend.md) v příkazu Declaration určuje, že k elementu lze přivodit z odvozených tříd nebo ze stejného sestavení, nebo obojí. Následující kód ukazuje ukázkovou `Protected Friend`ovou deklaraci:

```vb
Protected Friend stringForProjectAndHeirs As String
```

`Protected Friend` lze použít pouze na úrovni třídy a pouze v případě, že deklarujete člena třídy. To znamená, že můžete deklarovat chráněný element Friend ve třídě, ale ne na úrovni zdrojového souboru nebo oboru názvů, nebo uvnitř rozhraní, modulu, struktury nebo procedury.

## <a name="private"></a>Privátní

Klíčové slovo [Private](../../../language-reference/modifiers/private.md) v příkazu deklarace určuje, že element lze použít pouze v rámci stejného modulu, třídy nebo struktury. Následující kód ukazuje ukázkovou `Private`ovou deklaraci:

```vb
Private _numberForMeOnly As Integer
```

`Private` můžete použít jenom na úrovni modulu. To znamená, že můžete deklarovat privátní prvek uvnitř modulu, třídy nebo struktury, ale ne na úrovni zdrojového souboru nebo oboru názvů uvnitř rozhraní nebo v proceduře.

Na úrovni modulu je příkaz `Dim` bez klíčových slov úrovně přístupu ekvivalentní `Private` deklaraci. Můžete však chtít použít klíčové slovo `Private`, aby bylo snazší číst a interpretovat kód.

## <a name="private-protected"></a>Private Protected

Kombinace klíčového slova [Private Protected](../../../language-reference/modifiers/private-protected.md) v příkazu Declaration určuje, že k elementu lze získat pøístup pouze v rámci stejné třídy a také z odvozených tříd, které byly nalezeny ve stejném sestavení jako obsahující třídu. Modifikátor přístupu `Private Protected` je podporován od Visual Basic 15,5.

Následující příklad ukazuje `Private Protected` deklaraci:

```vb
Private Protected internalValue As Integer
```

Element `Private Protected` lze deklarovat pouze uvnitř třídy. Nelze jej deklarovat v rámci rozhraní nebo struktury, ani jej nelze deklarovat na úrovni zdrojového souboru nebo oboru názvů uvnitř rozhraní nebo struktury nebo v proceduře.

Modifikátor přístupu `Private Protected` je podporován Visual Basic 15,5 a novějším. Chcete-li jej použít, přidejte následující prvek do souboru Visual Basic projektu ( *\*. vbproj*). Pokud je v systému nainstalovaná Visual Basic 15,5 nebo novější, umožní vám využít všechny jazykové funkce podporované nejnovější verzí Visual Basic kompilátoru:

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

Chcete-li použít modifikátor přístupu `Private Protected`, je nutné přidat následující prvek do souboru projektu Visual Basic ( *\*. vbproj*):

```xml
<PropertyGroup>
   <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

Další informace najdete v tématu [nastavení jazykové verze Visual Basic](../../../language-reference/configure-language-version.md).

## <a name="access-modifiers"></a>Modifikátory přístupu

Klíčová slova, která určují úroveň přístupu, se nazývají *modifikátory přístupu*. Následující tabulka porovnává modifikátory přístupu:

|Modifikátor přístupu|Úroveň přístupu udělena|Prvky, které můžete deklarovat s touto úrovní přístupu|Kontext deklarace, ve kterém můžete použít tento modifikátor|
|---------------------|--------------------------|-----------------------------------------------------|----------------------------------------------------------------|
|`Public`|Neomezený<br /><br /> Jakýkoli kód, který může zobrazit veřejný prvek, má k němu přístup|Rozhraní<br /><br /> Moduly<br /><br /> Třídy<br /><br /> Struktury<br /><br /> Členové struktury<br /><br /> Procedury<br /><br /> Vlastnosti<br /><br /> Proměnné členů<br /><br /> Konstanty<br /><br /> Výčty<br /><br /> Události<br /><br /> Externí deklarace<br /><br /> Delegáti|Zdrojový soubor<br /><br /> Obor názvů<br /><br /> Rozhraní<br /><br /> Modul<br /><br /> Třída<br /><br /> Struktura|
|`Protected`|Odvození:<br /><br /> Kód ve třídě, která deklaruje chráněný element nebo třídu odvozenou z něj, může přistupovat k elementu.|Rozhraní<br /><br /> Třídy<br /><br /> Struktury<br /><br /> Procedury<br /><br /> Vlastnosti<br /><br /> Proměnné členů<br /><br /> Konstanty<br /><br /> Výčty<br /><br /> Události<br /><br /> Externí deklarace<br /><br /> Delegáti|Třída|
|`Friend`|Sestavení:<br /><br /> Kód v sestavení, který deklaruje element typu Friend, k němu má přístup|Rozhraní<br /><br /> Moduly<br /><br /> Třídy<br /><br /> Struktury<br /><br /> Členové struktury<br /><br /> Procedury<br /><br /> Vlastnosti<br /><br /> Proměnné členů<br /><br /> Konstanty<br /><br /> Výčty<br /><br /> Události<br /><br /> Externí deklarace<br /><br /> Delegáti|Zdrojový soubor<br /><br /> Obor názvů<br /><br /> Rozhraní<br /><br /> Modul<br /><br /> Třída<br /><br /> Struktura|
|`Protected``Friend`|Sjednocení `Protected` a `Friend`:<br /><br /> Kód ve stejné třídě nebo stejném sestavení jako chráněný Friend element nebo v rámci libovolné třídy odvozené z třídy elementu může k němu přistupovat.|Rozhraní<br /><br /> Třídy<br /><br /> Struktury<br /><br /> Procedury<br /><br /> Vlastnosti<br /><br /> Proměnné členů<br /><br /> Konstanty<br /><br /> Výčty<br /><br /> Události<br /><br /> Externí deklarace<br /><br /> Delegáti|Třída|
|`Private`|Kontext deklarace:<br /><br /> Kód v typu, který deklaruje soukromý element, včetně kódu v rámci obsažených typů, má přístup k elementu.|Rozhraní<br /><br /> Třídy<br /><br /> Struktury<br /><br /> Členové struktury<br /><br /> Procedury<br /><br /> Vlastnosti<br /><br /> Proměnné členů<br /><br /> Konstanty<br /><br /> Výčty<br /><br /> Události<br /><br /> Externí deklarace<br /><br /> Delegáti|Modul<br /><br /> Třída<br /><br /> Struktura|
|`Private Protected`|Kód ve třídě, která deklaruje soukromý chráněný element, nebo kód v odvozené třídě, který byl nalezen ve stejném sestavení jako třída bas.|Rozhraní<br /><br /> Třídy<br /><br /> Struktury<br /><br /> Procedury<br /><br /> Vlastnosti<br /><br /> Proměnné členů<br /><br /> Konstanty<br /><br /> Výčty<br /><br /> Události<br /><br /> Externí deklarace<br /><br /> Delegáti|Třída|

## <a name="see-also"></a>Viz také:

- [Příkaz Dim](../../../language-reference/statements/dim-statement.md)
- [Static](../../../language-reference/modifiers/static.md)
- [Deklarované názvy elementů](declared-element-names.md)
- [Odkazy na deklarované elementy](references-to-declared-elements.md)
- [Deklarované charakteristiky elementů](declared-element-characteristics.md)
- [Doba života v Visual Basic](lifetime.md)
- [Obor v Visual Basic](scope.md)
- [Postupy: Řízení dostupnosti proměnné](how-to-control-the-availability-of-a-variable.md)
- [Proměnné](../variables/index.md)
- [Deklarace proměnné](../variables/variable-declaration.md)
