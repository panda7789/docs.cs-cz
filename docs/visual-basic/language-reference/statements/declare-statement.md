---
title: "Declare – příkaz"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Declare
- vb.Lib
- vb.Any
helpviewer_keywords:
- Lib keyword [Visual Basic]
- declaring procedures [Visual Basic], Declare statement
- functions [Visual Basic], function procedures
- declarations [Visual Basic], procedures
- procedures [Visual Basic], declaration
- procedures [Visual Basic], external
- Alias keyword [Visual Basic]
- external references [Visual Basic], Visual Basic
- DLLs, declaring procedures
- Declare statement [Visual Basic]
- declarations [Visual Basic], external
- Visual Basic code, Function procedures
- As keyword [Visual Basic], in Declare statement
- resources [Visual Basic], declaring
- Public keyword [Visual Basic], Declare statement
- platform invoke, Visual Basic external references
- Sub procedures [Visual Basic], declarations
- APIs, declaring API functions
- Visual Basic code, Sub procedures
- Function procedures [Visual Basic], declaring
ms.assetid: d3f21fb0-b804-4c99-97ed-583b23894cf1
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2560f34a5130ef7453b50ffb4495b67bf1dfa4c8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="declare-statement"></a>Declare – příkaz
Deklaruje odkaz na procedury implementované v externí soubor.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ Overloads ] _  
Declare [ charsetmodifier ] [ Sub ] name Lib "libname" _  
[ Alias "aliasname" ] [ ([ parameterlist ]) ]  
' -or-  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ Overloads ] _  
Declare [ charsetmodifier ] [ Function ] name Lib "libname" _  
[ Alias "aliasname" ] [ ([ parameterlist ]) ] [ As returntype ]  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`attributelist`|Volitelné. V tématu [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|Volitelné. Může být jedna z následujících akcí:<br /><br /> -   [Veřejné](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Chráněný](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Privátní](../../../visual-basic/language-reference/modifiers/private.md)<br />-   `Protected Friend`<br /><br /> V tématu [úrovně v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Volitelné. V tématu [stínů](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`charsetmodifier`|Volitelné. Určuje znakovou sadu a soubor hledat informace. Může být jedna z následujících akcí:<br /><br /> -   [ANSI](../../../visual-basic/language-reference/modifiers/ansi.md) (výchozí)<br />-   [Kódování Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)<br />-   [Automaticky](../../../visual-basic/language-reference/modifiers/auto.md)|  
|`Sub`|Volitelné, ale buď `Sub` nebo `Function` musí zobrazit. Označuje, že externí procedura nevrací hodnotu.|  
|`Function`|Volitelné, ale buď `Sub` nebo `Function` musí zobrazit. Označuje, že externí procedura vrátí hodnotu.|  
|`name`|Požadováno. Název tohoto externího odkazu. Další informace najdete v tématu [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Lib`|Požadováno. Zavádí `Lib` klauzuli, která identifikuje externí soubor (DLL nebo zdroje), který obsahuje externí procedura.|  
|`libname`|Požadováno. Název souboru, který obsahuje deklarované postup.|  
|`Alias`|Volitelné. Označuje, že název zadaný v nelze postup probíhá v rámci svého souboru identifikovat `name`. Zadejte jeho identifikaci v `aliasname`.|  
|`aliasname`|Vyžaduje, pokud použijete `Alias` – klíčové slovo. Řetězec, který identifikuje podle postupu v jedním ze dvou způsobů:<br /><br /> Název vstupního bodu procedury v rámci svého souboru v uvozovkách (`""`)<br /><br /> -nebo-<br /><br /> Znaménko čísla (`#`) následuje celé číslo určující počet pořadí vstupní bod procedury v rámci svého souboru|  
|`parameterlist`|Vyžaduje, pokud, které procedura používá parametry. V tématu [seznam parametrů](../../../visual-basic/language-reference/statements/parameter-list.md).|  
|`returntype`|Požadováno pokud `Function` je zadán a `Option Strict` je `On`. Datový typ hodnoty vrácené procedurou.|  
  
## <a name="remarks"></a>Poznámky  
 V některých případech budete muset volání procedury definované v souboru (například DLL nebo zdroje) mimo projekt. Když to uděláte, Visual Basic – kompilátor nemá přístup k informacím, které potřebuje voláním procedury správně, například kde se nachází postup, jak je identifikovat, jeho volací sekvence a návratový typ a řetězec znaková sada, kterou používá. `Declare` Příkaz vytvoří odkaz na externí procedura a poskytuje tyto nezbytné informace.  
  
 Můžete použít `Declare` jenom na úrovni modulu. To znamená *deklarace kontextu* externího odkazu musí být třída, struktura nebo modul a nemůže být zdrojový soubor, obor názvů, rozhraní, postup nebo bloku. Další informace najdete v tématu [kontexty deklarace a výchozí úrovně přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Externí odkazuje na výchozí nastavení [veřejné](../../../visual-basic/language-reference/modifiers/public.md) přístup. Můžete nastavit jejich úrovně přístupu s modifikátory přístupu.  
  
## <a name="rules"></a>Pravidla  
  
-   **Atributy.** Atributy můžete použít pro externí odkaz. Všechny atributy, které použijete nemá vliv pouze v projektu, nikoli na externí soubor.  
  
-   **Modifikátory.** Externí postupy jsou implicitně [sdílené](../../../visual-basic/language-reference/modifiers/shared.md). Nelze použít `Shared` – klíčové slovo deklarace externí odkaz a nelze změnit jeho sdílený stav.  
  
     Externí procedura nemůže účastnit přepsání, implementace členů rozhraní nebo zpracování událostí. Podle toho, nelze použít `Overrides`, `Overridable`, `NotOverridable`, `MustOverride`, `Implements`, nebo `Handles` – klíčové slovo v `Declare` příkaz.  
  
-   **Externí procedura název.** Není nutné poskytnout tento externí odkaz se stejným názvem (v `name`) jako název vstupní bod procedury v rámci svého externího souboru (`aliasname`). Můžete použít `Alias` klauzule zadejte název vstupního bodu. To může být užitečné, pokud má stejný název jako vyhrazené modifikátor jazyka Visual Basic nebo proměnné, postup nebo jiné programovací element externí procedura ve stejném oboru.  
  
    > [!NOTE]
    >  Vstupní bod názvy ve většině knihovny DLL rozlišují malá a velká písmena.  
  
-   **Externí procedura číslo.** Alternativně můžete použít `Alias` klauzule k určení pořadí vstupního bodu export tabulky externího souboru. K tomuto účelu začnete `aliasname` znakem čísla (`#`). To může být užitečné, pokud není povolen libovolný znak v názvu externí procedura v jazyce Visual Basic, nebo pokud externí soubor exportuje postup bez názvu.  
  
## <a name="data-type-rules"></a>Datový typ pravidla  
  
-   **Datové typy parametrů.** Pokud `Option Strict` je `On`, musíte zadat datový typ jednotlivých parametrů v `parameterlist`. To může být jakýkoli datový typ nebo název výčtu, struktura, třídy nebo rozhraní. V rámci `parameterlist`, můžete použít `As` klauzule zadat datový typ argumentu mají být předány jednotlivé parametry.  
  
    > [!NOTE]
    >  Pokud externí procedura nebyla zapsána pro rozhraní .NET Framework, je nutné Ujistěte se, že odpovídají datové typy. Například, pokud je deklarovat externího odkazu na procedura Visual Basic 6.0 se `Integer` parametr (16 bitů v jazyce Visual Basic 6.0), je potřeba určit odpovídající argument jako `Short` v `Declare` příkaz, protože se jedná o 16 – bit typ integer v jazyce Visual Basic. Podobně `Long` má šířku různých dat v jazyce Visual Basic 6.0 a `Date` je implementováno jiným způsobem.  
  
-   **Návratový typ Data.** Pokud je externí procedura `Function` a `Option Strict` je `On`, musíte zadat datový typ hodnoty vrácené voláním kódu. To může být jakýkoli datový typ nebo název výčtu, struktura, třídy nebo rozhraní.  
  
    > [!NOTE]
    >  Visual Basic – kompilátor neověřuje, jestli vaše datové typy jsou kompatibilní s těmi, která externí procedury. Pokud došlo k neshodě, vygeneruje modul common language runtime <xref:System.Runtime.InteropServices.MarshalDirectiveException> výjimky za běhu.  
  
-   **Výchozí datové typy.** Pokud `Option Strict` je `Off` a nezadáte datový typ parametru v `parameterlist`, Visual Basic – kompilátor Převede argument odpovídající [Object – datový typ](../../../visual-basic/language-reference/data-types/object-data-type.md). Podobně pokud nezadáte `returntype`, kompilátor má návratový datový typ jako `Object`.  
  
    > [!NOTE]
    >  Vzhledem k tomu, že pracujete s externí postup, který může zapisovat na jiné platformě, je nebezpečné, aby všechny předpoklady o typech dat nebo a povolení jejich výchozí. Je mnohem bezpečnější určovat datový typ všechny parametry a návratové hodnoty, pokud existuje. To také zlepšuje čitelnost kódu.  
  
## <a name="behavior"></a>Chování  
  
-   **Rozsah.** Externí odkaz je v oboru v celé jeho třídy, struktury nebo modul.  
  
-   **Doba platnosti.** Externí odkaz má stejnou dobu života jako třída, struktura nebo modul, ve kterém je deklarovaná.  
  
-   **Volání externí procedura.** Volání externí procedura stejným způsobem jako zavoláte `Function` nebo `Sub` postup – s použitím ve výrazu, pokud vrátí hodnotu, nebo zadáním v [volání příkazu](../../../visual-basic/language-reference/statements/call-statement.md) Pokud nevrací hodnotu.  
  
     Předání argumentů externí procedura přesně podle specifikace `parameterlist` v `Declare` příkaz. Není vzít v úvahu jak parametry byly původně deklarovány v externím souboru. Podobně pokud návratovou hodnotu, použijte ji přesně podle specifikace `returntype` v `Declare` příkaz.  
  
-   **Znak sady.** Můžete zadat v `charsetmodifier` jak by měla jazyka Visual Basic zařazování řetězců při volání externí procedura. `Ansi` Modifikátor přesměruje jazyka Visual Basic přeuspořádat všechny řetězce na ANSI hodnoty a `Unicode` modifikátor přesměruje ho přeuspořádat všechny řetězce Unicode hodnoty. `Auto` Modifikátor přesměruje jazyka Visual Basic pro zařazování řetězců podle rozhraní .NET Framework pravidla, podle externího odkazu `name`, nebo `aliasname` -li zadána. Výchozí hodnota je `Ansi`.  
  
     `charsetmodifier`také určuje, jak Visual Basic vyhledat externí procedura v rámci svého externího souboru. `Ansi`a `Unicode` i přímé jazyka Visual Basic k vyhledání beze změny jeho názvu během hledání. `Auto`přesměruje jazyka Visual Basic určit základní znaková sada spuštění platformy a které by mohly mít změnit název externí procedura následujícím způsobem:  
  
    -   Na platformě ANSI, jako je například systém Windows 95, Windows 98 nebo Windows Millennium Edition nejprve vyhledejte externí procedura bez úprav název. Pokud to nepomůže, připojte na konec názvu externí procedura "A" a znovu vyhledat.  
  
    -   Na platformě znakové sady Unicode, jako je například systému Windows NT, Windows 2000 nebo Windows XP nejprve vyhledejte externí procedura bez úprav název. Pokud to nepomůže, připojit "W" na konec externí procedura název a znovu vyhledat.  
  
-   **Mechanismus.** Visual Basic používá rozhraní .NET Framework *vyvolání platformy* (kódu PInvoke) mechanismus vyřešit a získat přístup k externí postupy. `Declare` Příkaz a <xref:System.Runtime.InteropServices.DllImportAttribute> třída obou použít tento mechanismus automaticky a není nutné žádnou znalost PInvoke. Další informace najdete v tématu [návod: volání rozhraní API systému Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md).  
  
> [!IMPORTANT]
>  Pokud je externí procedura mimo modul CLR (CLR), je *nespravovaného kódu*. Při volání tento postup, například funkce Win32 API nebo metodu COM, mohou být vystaveny vaší aplikace na bezpečnostní rizika. Další informace najdete v tématu [zabezpečené kódování pokyny pro nespravovaného kódu](../../../framework/security/secure-coding-guidelines-for-unmanaged-code.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad deklaruje externí odkaz na `Function` procedury, která vrátí aktuální uživatelské jméno. Potom zavolá externí procedura `GetUserNameA` jako součást `getUser` postupu.  
  
 [!code-vb[VbVbalrStatements#15](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/declare-statement_1.vb)]  
  
## <a name="example"></a>Příklad  
 <xref:System.Runtime.InteropServices.DllImportAttribute> Poskytuje alternativní způsob použití funkce v nespravovaném kódu. Následující příklad deklaruje importované funkce bez použití `Declare` příkaz.  
  
 [!code-vb[VbVbalrStatements#16](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/declare-statement_2.vb)]  
  
 [!code-vb[VbVbalrStatements#1](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/declare-statement_3.vb)]  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>  
 [Imports – příkaz (Namespace .NET a typ)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [AddressOf – operátor](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [Function – příkaz](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Sub – příkaz](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Seznam parametrů](../../../visual-basic/language-reference/statements/parameter-list.md)  
 [Call – příkaz](../../../visual-basic/language-reference/statements/call-statement.md)  
 [Návod: Volání rozhraní API systému Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
