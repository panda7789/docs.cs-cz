---
title: Úrovně přístupu v jazyce Visual Basic
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
ms.openlocfilehash: 1e2d43f33a352d3f4502965c5368eb901e7bffdf
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2018
---
# <a name="access-levels-in-visual-basic"></a>Úrovně přístupu v jazyce Visual Basic
*Úroveň přístupu* deklarované elementu je v rozsahu možnost k němu přístup, to znamená, jaký kód má oprávnění číst nebo zapisovat do něj. Ten je daný nejen jak deklarovat elementu samotného, ale také úroveň přístupu tohoto kontejneru elementu. Kód, který nemůže získat přístup k elementu s obsahem. nemůžete použít žádnou z jeho prvky obsahují, i ty deklarován jako `Public`. Například `Public` v proměnné `Private` struktura je přístupná z uvnitř třídu, která obsahuje strukturu, ale nikoli z mimo třídy.  
  
## <a name="public"></a>Public  
 [Veřejné](../../../../visual-basic/language-reference/modifiers/public.md) – klíčové slovo v příkazu deklarace Určuje, že element je přístupný z kódu kamkoli ve stejném projektu, od jiné projekty, které odkazují na projektu a z libovolného sestavení vytvořené z projektu. Následující kód ukazuje ukázku `Public` deklarace.  
  
```vb  
Public Class classForEverybody  
```  
  
 Můžete použít `Public` pouze na úrovni modulu, rozhraní nebo obor názvů. To znamená, že je možné deklarovat veřejné element na úrovni zdrojový soubor nebo obor názvů, nebo uvnitř rozhraní, modulu, třídu nebo strukturu, ale ne v postupu.  
  
## <a name="protected"></a>Chráněno  
 [Chráněné](../../../../visual-basic/language-reference/modifiers/protected.md) – klíčové slovo v příkazu deklarace Určuje, že element lze přistupovat pouze z v rámci stejné třídy nebo z třídy odvozené z této třídy. Následující kód ukazuje ukázku `Protected` deklarace.  
  
```vb  
Protected Class classForMyHeirs  
```  
  
 Můžete použít `Protected` pouze na třídu úroveň a pouze když je deklarovat člena třídy. To znamená, že je možné deklarovat element chráněné v třídě, ale ne na úrovni zdrojový soubor nebo obor názvů nebo uvnitř rozhraní, modulu, struktura nebo postupu.  
  
## <a name="friend"></a>Friend  
 [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) – klíčové slovo v příkazu deklarace Určuje, že element lze přistupovat z v rámci stejného sestavení, ale nikoli z mimo sestavení. Následující kód ukazuje ukázku `Friend` deklarace.  
  
```vb  
Friend stringForThisProject As String  
```  
  
 Můžete použít `Friend` pouze na úrovni modulu, rozhraní nebo obor názvů. To znamená, že je možné deklarovat friend element na úrovni zdrojový soubor nebo obor názvů, nebo uvnitř rozhraní, modulu, třídu nebo strukturu, ale ne v postupu.  
  
## <a name="protected-friend"></a>Chráněné Friend  
 `Protected` a `Friend` klíčová slova společně v příkazu deklarace určete, že element budou mít přístup z odvozené třídy nebo v do stejného sestavení nebo obojí. Následující kód ukazuje ukázku `Protected Friend` deklarace.  
  
```vb  
Protected Friend stringForProjectAndHeirs As String  
```  
  
 Můžete použít `Protected Friend` pouze na třídu úroveň a pouze když je deklarovat člena třídy. To znamená, že je možné deklarovat element chráněné friend v třídě, ale ne na úrovni zdrojový soubor nebo obor názvů nebo uvnitř rozhraní, modulu, struktura nebo postupu.  
  
## <a name="private"></a>Soukromé  
 [Privátní](../../../../visual-basic/language-reference/modifiers/private.md) – klíčové slovo v příkazu deklarace Určuje, že element můžete přistupovat pouze z v rámci stejné modulu, třídu nebo strukturu. Následující kód ukazuje ukázku `Private` deklarace.  
  
```vb  
Private numberForMeOnly As Integer  
```  
  
 Můžete použít `Private` jenom na úrovni modulu. To znamená, že je možné deklarovat privátní element uvnitř modulu, třídu nebo strukturu, ale ne na úrovni zdrojový soubor nebo obor názvů, uvnitř rozhraní nebo v postupu.  
  
 Na úrovni modulu `Dim` je ekvivalentní příkaz bez jakékoli klíčová slova úrovně přístupu `Private` deklarace. Ale můžete chtít použít `Private` – klíčové slovo usnadnění kódu ke čtení a interpretovat.  

## <a name="private-protected"></a>Privátní chráněný

[Privátní chráněné](../../../language-reference/modifiers/private-protected.md) – klíčové slovo v příkazu deklarace Určuje, že element můžete přistupovat pouze z v rámci stejné třídy a také z nalezené ve stejném sestavení jako obsahující třídy odvozené třídy. `Private Protected` – Modifikátor přístupu je podporovaná počínaje 15,5 Visual Basic.

Následující příklad ukazuje `Private Protected` deklarace:

```vb
Private Protected internalValue As Integer
```

Je možné deklarovat `Private Protected` element pouze uvnitř třídy. V rámci rozhraním nebo struktury nelze deklarovat ho ani můžete je deklarovat ho na úrovni zdrojový soubor nebo obor názvů, uvnitř rozhraní nebo strukturu, nebo v postupu.

`Private Protected` – Modifikátor přístupu jsou podporovány nástrojem 15,5 Visual Basic a vyšší. Pokud chcete použít, přidejte následující prvek se v souboru projektu (*.vbproj) jazyka Visual Basic. Jak dlouho jako 15,5 Visual Basic nebo novější je nainstalován ve vašem systému, umožňuje využít výhod všech funkcí jazyka nejnovější verze kompilátoru jazyka Visual Basic nepodporuje:

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

Použít `Private Protected` – modifikátor přístupu, musíte do souboru projektu (*.vbproj) a Visual Basic přidat následující element:

```xml
<PropertyGroup>
   <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

 ## <a name="access-modifiers"></a>Modifikátory přístupu  
 Klíčová slova, které určují úroveň přístupu, se nazývají *přístup modifikátory*. Následující tabulka porovnává modifikátory přístupu.  
  
|Modifikátor přístupu|Úroveň přístupu uděleno|Prvky, které můžou deklarovat s touto úrovní přístupu|Deklarace kontext, ve kterém můžete použít tento modifikátor|  
|---------------------|--------------------------|-----------------------------------------------------|----------------------------------------------------------------|  
|`Public`|Neomezený:<br /><br /> Kód, který veřejné elementu k němu přístup|Rozhraní<br /><br /> Moduly<br /><br /> Třídy<br /><br /> Struktury<br /><br /> Členové struktury<br /><br /> Procedury<br /><br /> Vlastnosti<br /><br /> Členské proměnné<br /><br /> Konstanty<br /><br /> Výčty<br /><br /> Události<br /><br /> Externí deklarace<br /><br /> Delegáty|Zdrojový soubor<br /><br /> Obor názvů<br /><br /> Rozhraní<br /><br /> Modul<br /><br /> Třída<br /><br /> Struktura|  
|`Protected`|Derivational:<br /><br /> Kód ve třídě, který deklaruje, že chráněný element nebo třídy odvozené z něj, můžete přístup k elementu|Rozhraní<br /><br /> Třídy<br /><br /> Struktury<br /><br /> Procedury<br /><br /> Vlastnosti<br /><br /> Členské proměnné<br /><br /> Konstanty<br /><br /> Výčty<br /><br /> Události<br /><br /> Externí deklarace<br /><br /> Delegáty|Třída|  
|`Friend`|Sestavení:<br /><br /> Kód v sestavení, který deklaruje, že friend element k němu přístup|Rozhraní<br /><br /> Moduly<br /><br /> Třídy<br /><br /> Struktury<br /><br /> Členové struktury<br /><br /> Procedury<br /><br /> Vlastnosti<br /><br /> Členské proměnné<br /><br /> Konstanty<br /><br /> Výčty<br /><br /> Události<br /><br /> Externí deklarace<br /><br /> Delegáty|Zdrojový soubor<br /><br /> Obor názvů<br /><br /> Rozhraní<br /><br /> Modul<br /><br /> Třída<br /><br /> Struktura|  
|`Protected``Friend`|Union z `Protected` a `Friend`:<br /><br /> Kód na stejné třídy nebo do stejného sestavení jako element chráněné friend nebo v jakékoli třídy odvozené od třídy elementu, k němu přístup|Rozhraní<br /><br /> Třídy<br /><br /> Struktury<br /><br /> Procedury<br /><br /> Vlastnosti<br /><br /> Členské proměnné<br /><br /> Konstanty<br /><br /> Výčty<br /><br /> Události<br /><br /> Externí deklarace<br /><br /> Delegáty|Třída|  
|`Private`|Kontext deklarace:<br /><br /> Kód v typu, který deklaruje, že privátní element, včetně kódu v rámci omezením typů, můžete přístup k elementu|Rozhraní<br /><br /> Třídy<br /><br /> Struktury<br /><br /> Členové struktury<br /><br /> Procedury<br /><br /> Vlastnosti<br /><br /> Členské proměnné<br /><br /> Konstanty<br /><br /> Výčty<br /><br /> Události<br /><br /> Externí deklarace<br /><br /> Delegáty|Modul<br /><br /> Třída<br /><br /> Struktura|
|`Private Protected`|Kód ve třídě, který deklaruje element privátní chráněný, nebo kód v odvozené třídě najít ve stejném sestavení jako třída bas.|Rozhraní<br /><br /> Třídy<br /><br /> Struktury<br /><br /> Procedury<br /><br /> Vlastnosti<br /><br /> Členské proměnné<br /><br /> Konstanty<br /><br /> Výčty<br /><br /> Události<br /><br /> Externí deklarace<br /><br /> Delegáty|Třída|
  
## <a name="see-also"></a>Viz také  
 [Příkaz Dim](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [Static](../../../../visual-basic/language-reference/modifiers/static.md)  
 [Deklarované názvy elementů](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [Odkazy na deklarované elementy](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Deklarované charakteristiky elementů](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [Doba platnosti v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [Rozsah v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)  
 [Postupy: Řízení dostupnosti proměnné](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-availability-of-a-variable.md)  
 [Proměnné](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [Deklarace proměnné](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
