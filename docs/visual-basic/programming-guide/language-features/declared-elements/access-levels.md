---
title: "Úrovně přístupu v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- members [Visual Basic], accessing in Visual Basic
- Friend access modifier
- access levels, declared elements
- access levels
- access modifiers
- Public access modifier
- Protected access modifier
- Protected Friend access modifier
- Private access modifier
- declared elements [Visual Basic], access level
ms.assetid: 6e06c1ab-fd78-47f0-83a8-1152780b5e1a
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 87e43ac7e813cece1179bdaf24c86fa62adcb438
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="access-levels-in-visual-basic"></a>Úrovně přístupu v jazyce Visual Basic
*Úroveň přístupu* deklarované elementu je v rozsahu možnost k němu přístup, to znamená, jaký kód má oprávnění číst nebo zapisovat do něj. Ten je daný nejen jak deklarovat elementu samotného, ale také úroveň přístupu tohoto kontejneru elementu. Kód, který nemůže získat přístup k elementu s obsahem. nemůžete použít žádnou z jeho prvky obsahují, i ty deklarován jako `Public`. Například `Public` v proměnné `Private` struktura je přístupná z uvnitř třídu, která obsahuje strukturu, ale nikoli z mimo třídy.  
  
## <a name="public"></a>Public  
 [Veřejné](../../../../visual-basic/language-reference/modifiers/public.md) – klíčové slovo v příkazu deklarace Určuje, zda elementy přístupná z kódu kamkoli ve stejném projektu, od jiné projekty, které odkazují na projektu a z libovolného sestavení vytvořené z projektu. Následující kód ukazuje ukázku `Public` deklarace.  
  
```  
Public Class classForEverybody  
```  
  
 Můžete použít `Public` pouze na úrovni modulu, rozhraní nebo obor názvů. To znamená, že je možné deklarovat veřejné element na úrovni zdrojový soubor nebo obor názvů, nebo uvnitř rozhraní, modulu, třídu nebo strukturu, ale ne v postupu.  
  
## <a name="protected"></a>Chráněno  
 [Chráněné](../../../../visual-basic/language-reference/modifiers/protected.md) – klíčové slovo v příkazu deklarace Určuje, že elementy lze přistupovat pouze z v rámci stejné třídy nebo z třídy odvozené z této třídy. Následující kód ukazuje ukázku `Protected` deklarace.  
  
```  
Protected Class classForMyHeirs  
```  
  
 Můžete použít `Protected` pouze na třídu úroveň a pouze když je deklarovat člena třídy. To znamená, že je možné deklarovat element chráněné v třídě, ale ne na úrovni zdrojový soubor nebo obor názvů nebo uvnitř rozhraní, modulu, struktura nebo postupu.  
  
## <a name="friend"></a>Friend  
 [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) – klíčové slovo v příkazu deklarace Určuje, že elementy lze přistupovat z v rámci stejného sestavení, ale nikoli z mimo sestavení. Následující kód ukazuje ukázku `Friend` deklarace.  
  
```  
Friend stringForThisProject As String  
```  
  
 Můžete použít `Friend` pouze na úrovni modulu, rozhraní nebo obor názvů. To znamená, že je možné deklarovat friend element na úrovni zdrojový soubor nebo obor názvů, nebo uvnitř rozhraní, modulu, třídu nebo strukturu, ale ne v postupu.  
  
## <a name="protected-friend"></a>Chráněné Friend  
 `Protected` a `Friend` klíčová slova společně v příkazu deklarace určete, zda prvky budou mít přístup z odvozené třídy nebo v do stejného sestavení nebo obojí. Následující kód ukazuje ukázku `Protected Friend` deklarace.  
  
```  
Protected Friend stringForProjectAndHeirs As String  
```  
  
 Můžete použít `Protected Friend` pouze na třídu úroveň a pouze když je deklarovat člena třídy. To znamená, že je možné deklarovat element chráněné friend v třídě, ale ne na úrovni zdrojový soubor nebo obor názvů nebo uvnitř rozhraní, modulu, struktura nebo postupu.  
  
## <a name="private"></a>Soukromé  
 [Privátní](../../../../visual-basic/language-reference/modifiers/private.md) – klíčové slovo v příkazu deklarace Určuje, že prvky můžete přistupovat pouze z v rámci stejné modulu, třídu nebo strukturu. Následující kód ukazuje ukázku `Private` deklarace.  
  
```  
Private numberForMeOnly As Integer  
```  
  
 Můžete použít `Private` jenom na úrovni modulu. To znamená, že je možné deklarovat privátní element uvnitř modulu, třídu nebo strukturu, ale ne na úrovni zdrojový soubor nebo obor názvů, uvnitř rozhraní nebo v postupu.  
  
 Na úrovni modulu `Dim` je ekvivalentní příkaz bez jakékoli klíčová slova úrovně přístupu `Private` deklarace. Ale můžete chtít použít `Private` – klíčové slovo usnadnění kódu ke čtení a interpretovat.  
  
## <a name="access-modifiers"></a>Modifikátory přístupu  
 Klíčová slova, které určují úroveň přístupu, se nazývají *přístup modifikátory*. Následující tabulka porovnává modifikátory přístupu.  
  
|Modifikátor přístupu|Úroveň přístupu uděleno|Prvky, které můžou deklarovat s touto úrovní přístupu|Deklarace kontext, ve kterém můžete použít tento modifikátor|  
|---------------------|--------------------------|-----------------------------------------------------|----------------------------------------------------------------|  
|`Public`|Neomezený:<br /><br /> Kód, který veřejné elementu k němu přístup|Rozhraní<br /><br /> Moduly<br /><br /> Třídy<br /><br /> Struktury<br /><br /> Členové struktury<br /><br /> Procedury<br /><br /> Vlastnosti<br /><br /> Členské proměnné<br /><br /> Konstanty<br /><br /> Výčty<br /><br /> Události<br /><br /> Externí deklarace<br /><br /> Delegáty|Zdrojový soubor<br /><br /> Obor názvů<br /><br /> Rozhraní<br /><br /> Modul<br /><br /> Třída<br /><br /> Struktura|  
|`Protected`|Derivational:<br /><br /> Kód ve třídě, který deklaruje, že chráněný element nebo třídy odvozené z něj, můžete přístup k elementu|Rozhraní<br /><br /> Třídy<br /><br /> Struktury<br /><br /> Procedury<br /><br /> Vlastnosti<br /><br /> Členské proměnné<br /><br /> Konstanty<br /><br /> Výčty<br /><br /> Události<br /><br /> Externí deklarace<br /><br /> Delegáty|Třída|  
|`Friend`|Sestavení:<br /><br /> Kód v sestavení, který deklaruje, že friend element k němu přístup|Rozhraní<br /><br /> Moduly<br /><br /> Třídy<br /><br /> Struktury<br /><br /> Členové struktury<br /><br /> Procedury<br /><br /> Vlastnosti<br /><br /> Členské proměnné<br /><br /> Konstanty<br /><br /> Výčty<br /><br /> Události<br /><br /> Externí deklarace<br /><br /> Delegáty|Zdrojový soubor<br /><br /> Obor názvů<br /><br /> Rozhraní<br /><br /> Modul<br /><br /> Třída<br /><br /> Struktura|  
|`Protected``Friend`|Union z `Protected` a `Friend`:<br /><br /> Kód na stejné třídy nebo do stejného sestavení jako element chráněné friend nebo v jakékoli třídy odvozené od třídy elementu, k němu přístup|Rozhraní<br /><br /> Třídy<br /><br /> Struktury<br /><br /> Procedury<br /><br /> Vlastnosti<br /><br /> Členské proměnné<br /><br /> Konstanty<br /><br /> Výčty<br /><br /> Události<br /><br /> Externí deklarace<br /><br /> Delegáty|Třída|  
|`Private`|Kontext deklarace:<br /><br /> Kód v typu, který deklaruje, že privátní element, včetně kódu v rámci omezením typů, můžete přístup k elementu|Rozhraní<br /><br /> Třídy<br /><br /> Struktury<br /><br /> Členové struktury<br /><br /> Procedury<br /><br /> Vlastnosti<br /><br /> Členské proměnné<br /><br /> Konstanty<br /><br /> Výčty<br /><br /> Události<br /><br /> Externí deklarace<br /><br /> Delegáty|Modul<br /><br /> Třída<br /><br /> Struktura|  
  
## <a name="see-also"></a>Viz také  
 [Dim – příkaz](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [Statické](../../../../visual-basic/language-reference/modifiers/static.md)  
 [Deklarované názvy elementů](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [Odkazy na deklarované elementy](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Deklarované charakteristiky elementu](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [Doba platnosti v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [Rozsah v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)  
 [Postupy: řízení dostupnosti proměnné](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-availability-of-a-variable.md)  
 [Proměnné](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [Deklarace proměnné](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
