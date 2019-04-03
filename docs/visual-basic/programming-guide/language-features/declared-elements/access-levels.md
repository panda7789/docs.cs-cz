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
ms.openlocfilehash: d8f2f16d2fb15f2e840f13f177d3fea83fda315e
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843092"
---
# <a name="access-levels-in-visual-basic"></a>Úrovně přístupu v jazyce Visual Basic
*Úroveň přístupu* deklarované elementu je rozsah schopnost k němu přístup, to znamená, jaký kód má oprávnění k jeho čtení nebo zápis do něj. To je určen pouze tak, jak deklarovat samotného elementu, ale také podle úrovně přístupu k elementu kontejneru. Kód, který nemá přístup k elementu s obsahem nelze použít žádnou z jeho elementů obsažených, včetně těch deklarován jako `Public`. Například `Public` v proměnné `Private` struktury lze přistupovat z uvnitř třídy, která obsahuje strukturu, ale ne z vně třídy.  
  
## <a name="public"></a>Public  
 [Veřejné](../../../../visual-basic/language-reference/modifiers/public.md) – klíčové slovo v příkazu deklarace. Určuje, že element je přístupný z kódu kdekoli ve stejném projektu, než ostatní projekty, které odkazují na projekt a z libovolné sestavení vytvořeného z projektu. Následující kód ukazuje ukázku `Public` deklarace.  
  
```vb  
Public Class classForEverybody  
```  
  
 Můžete použít `Public` pouze na úrovni modulu, rozhraní nebo oboru názvů. To znamená, že je možné deklarovat veřejného elementu na úrovni zdrojového souboru nebo oboru názvů, nebo uvnitř rozhraní, modulu, třídy nebo struktury, ale ne v postupu.  
  
## <a name="protected"></a>Chráněno  
 [Chráněné](../../../../visual-basic/language-reference/modifiers/protected.md) – klíčové slovo v příkazu deklarace. Určuje, že element je přístupný pouze z v rámci stejné třídy nebo z třídy odvozené z této třídy. Následující kód ukazuje ukázku `Protected` deklarace.  
  
```vb  
Protected Class classForMyHeirs  
```  
  
 Můžete použít `Protected` pouze na třídu úrovni a pouze pokud deklarujete člena třídy. To znamená, že je možné deklarovat element chráněné ve třídě, ale ne na úrovni zdrojového souboru nebo oboru názvů nebo v rámci rozhraní, modul, struktury nebo proceduru.  
  
## <a name="friend"></a>Friend  
 [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) – klíčové slovo v příkazu deklarace. Určuje, že element je přístupný z v rámci stejného sestavení, ale ne z mimo sestavení. Následující kód ukazuje ukázku `Friend` deklarace.  
  
```vb  
Friend stringForThisProject As String  
```  
  
 Můžete použít `Friend` pouze na úrovni modulu, rozhraní nebo oboru názvů. To znamená, že je možné deklarovat spřátelenou elementu na úrovni zdrojového souboru nebo oboru názvů, nebo uvnitř rozhraní, modulu, třídy nebo struktury, ale ne v postupu.  
  
## <a name="protected-friend"></a>Chráněné typu Friend  
 [Protected Friend](../../../language-reference/modifiers/protected-friend.md) – kombinace klíčových slov v příkazu deklarace. Určuje, že element je přístupný z odvozených tříd nebo v rámci stejného sestavení, nebo obojí. Následující kód ukazuje ukázku `Protected Friend` deklarace.  
  
```vb  
Protected Friend stringForProjectAndHeirs As String  
```  
  
 Můžete použít `Protected Friend` pouze na třídu úrovni a pouze pokud deklarujete člena třídy. To znamená, že je možné deklarovat element chráněné friend ve třídě, ale ne na úrovni zdrojového souboru nebo oboru názvů nebo v rámci rozhraní, modul, struktury nebo proceduru.  
  
## <a name="private"></a>Soukromé  
 [Privátní](../../../../visual-basic/language-reference/modifiers/private.md) – klíčové slovo v příkazu deklarace. Určuje, že element je přístupný pouze z v rámci stejného modulu, třídy nebo struktury. Následující kód ukazuje ukázku `Private` deklarace.  
  
```vb  
Private numberForMeOnly As Integer  
```  
  
 Můžete použít `Private` pouze na úrovni modulu. To znamená, že je možné deklarovat soukromé prvek uvnitř modulu, třídy nebo struktury, ale ne na úrovni zdrojového souboru nebo oboru názvů, uvnitř rozhraní nebo v postupu.  
  
 Na úrovni modulu `Dim` příkaz bez jakékoli klíčová slova úroveň přístupu je ekvivalentní `Private` deklarace. Však můžete chtít použít `Private` – klíčové slovo, aby váš kód lépe čitelný a pochopitelný.  

## <a name="private-protected"></a>Privátní, chráněné

[Private Protected](../../../language-reference/modifiers/private-protected.md) – kombinace klíčových slov v příkazu deklarace. Určuje, že element je přístupný pouze z v rámci stejné třídy a také z odvozené třídy v rámci stejného sestavení jako třídu obsahující. `Private Protected` Modifikátor přístupu se podporuje od verze 15.5 jazyka Visual Basic.

Následující příklad ukazuje `Private Protected` deklarace:

```vb
Private Protected internalValue As Integer
```

Je možné deklarovat `Private Protected` element pouze uvnitř třídy. Ho nemůže deklarovat v rámci rozhraní nebo struktura, ani můžete je deklarovat ji na úrovni zdrojového souboru nebo oboru názvů, uvnitř rozhraní nebo struktura, nebo postup.

`Private Protected` Modifikátor přístupu je podporován v jazyce Visual Basic 15.5 nebo novější. Ho Pokud chcete použít, přidejte následující prvek do souboru projektu (*.vbproj) jazyka Visual Basic. Jak dlouho jako 15.5 jazyka Visual Basic nebo vyšší je nainstalovaný ve vašem systému, umožňuje využít výhod všech funkcí jazyka podporovaná modulem nejnovější verzi kompilátoru jazyka Visual Basic:

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

Použít `Private Protected` modifikátor přístupu, je nutné přidat následující element do souboru projektu (*.vbproj) jazyka Visual Basic:

```xml
<PropertyGroup>
   <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

Další informace najdete v části [nastavení verze jazyka Visual Basic](../../../language-reference/configure-language-version.md).

## <a name="access-modifiers"></a>Modifikátory přístupu  

Klíčová slova, které určují úroveň přístupu se nazývají *modifikátorů přístupu*. Následující tabulka porovnává modifikátory přístupu.  
  
|Modifikátor přístupu|Úroveň přístupu uděleného|Prvky, které je možné deklarovat s touto úrovní přístupu|Deklarace kontextu, ve kterém můžete použít tento modifikátor|  
|---------------------|--------------------------|-----------------------------------------------------|----------------------------------------------------------------|  
|`Public`|Neomezený:<br /><br /> Veškerý kód, který můžete zobrazit veřejné element k němu přístup|Rozhraní<br /><br /> Moduly<br /><br /> Třídy<br /><br /> Struktury<br /><br /> Členové struktury<br /><br /> Procedury<br /><br /> Vlastnosti<br /><br /> Členské proměnné<br /><br /> Konstanty<br /><br /> Výčty<br /><br /> Události<br /><br /> Externí deklarace<br /><br /> Delegáty|Zdrojový soubor<br /><br /> Obor názvů<br /><br /> Rozhraní<br /><br /> Modul<br /><br /> Třída<br /><br /> Struktura|  
|`Protected`|Derivational:<br /><br /> Kód ve třídě, která deklaruje element chráněné nebo třídu odvozenou z něj, můžete přístup k elementu|Rozhraní<br /><br /> Třídy<br /><br /> Struktury<br /><br /> Procedury<br /><br /> Vlastnosti<br /><br /> Členské proměnné<br /><br /> Konstanty<br /><br /> Výčty<br /><br /> Události<br /><br /> Externí deklarace<br /><br /> Delegáty|Třída|  
|`Friend`|Sestavení:<br /><br /> Kód v sestavení, která deklaruje, že k němu mají přístup typu friend element|Rozhraní<br /><br /> Moduly<br /><br /> Třídy<br /><br /> Struktury<br /><br /> Členové struktury<br /><br /> Procedury<br /><br /> Vlastnosti<br /><br /> Členské proměnné<br /><br /> Konstanty<br /><br /> Výčty<br /><br /> Události<br /><br /> Externí deklarace<br /><br /> Delegáty|Zdrojový soubor<br /><br /> Obor názvů<br /><br /> Rozhraní<br /><br /> Modul<br /><br /> Třída<br /><br /> Struktura|  
|`Protected``Friend`|Sjednocení se `Protected` a `Friend`:<br /><br /> Kód ve stejné třídě nebo stejného sestavení jako prvek chráněné friend nebo v libovolné třídě odvozené z třídy prvku, k němu máte přístup|Rozhraní<br /><br /> Třídy<br /><br /> Struktury<br /><br /> Procedury<br /><br /> Vlastnosti<br /><br /> Členské proměnné<br /><br /> Konstanty<br /><br /> Výčty<br /><br /> Události<br /><br /> Externí deklarace<br /><br /> Delegáty|Třída|  
|`Private`|Kontext deklarace:<br /><br /> Kód v typu, který deklaruje element privátní, včetně kódu v rámci omezením typů, můžete získat přístup k elementu|Rozhraní<br /><br /> Třídy<br /><br /> Struktury<br /><br /> Členové struktury<br /><br /> Procedury<br /><br /> Vlastnosti<br /><br /> Členské proměnné<br /><br /> Konstanty<br /><br /> Výčty<br /><br /> Události<br /><br /> Externí deklarace<br /><br /> Delegáty|Modul<br /><br /> Třída<br /><br /> Struktura|
|`Private Protected`|Kód ve třídě, která deklaruje element privátní chráněný, nebo kód v odvozené třídě nalezen ve stejném sestavení jako třída bas.|Rozhraní<br /><br /> Třídy<br /><br /> Struktury<br /><br /> Procedury<br /><br /> Vlastnosti<br /><br /> Členské proměnné<br /><br /> Konstanty<br /><br /> Výčty<br /><br /> Události<br /><br /> Externí deklarace<br /><br /> Delegáty|Třída|
  
## <a name="see-also"></a>Viz také:

- [Příkaz Dim](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [Static](../../../../visual-basic/language-reference/modifiers/static.md)
- [Deklarované názvy elementů](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Odkazy na deklarované elementy](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Deklarované charakteristiky elementů](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [Doba platnosti v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [Obor v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [Postupy: Řízení dostupnosti proměnné](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-availability-of-a-variable.md)
- [Proměnné](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [Deklarace proměnné](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
