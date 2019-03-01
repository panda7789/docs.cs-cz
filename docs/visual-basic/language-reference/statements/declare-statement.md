---
title: Declare – příkaz (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 4a2e1704e72e608f5b5fd9c6dace42c144f92bb4
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56973168"
---
# <a name="declare-statement"></a>Declare – příkaz
Deklaruje odkaz na proceduru implementovanou v externím souboru.  
  
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
|`attributelist`|Volitelné. Zobrazit [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|Volitelné. Může být jedna z následujících akcí:<br /><br /> -   [Veřejné](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend –](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Privátní](../../../visual-basic/language-reference/modifiers/private.md)<br />- [Chráněné typu Friend](../../language-reference/modifiers/protected-friend.md)<br />- [Privátní, chráněné](../../language-reference/modifiers/private-protected.md)<br /><br /> Zobrazit [úrovní v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Volitelné. Zobrazit [stíny](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`charsetmodifier`|Volitelné. Určuje znakovou sadou a soubor vyhledat informace. Může být jedna z následujících akcí:<br /><br /> -   [ANSI](../../../visual-basic/language-reference/modifiers/ansi.md) (výchozí)<br />-   [Kódování Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)<br />-   [Auto](../../../visual-basic/language-reference/modifiers/auto.md)|  
|`Sub`|Volitelné, ale buď `Sub` nebo `Function` musí být uvedena. Označuje, že externí procedura nesmí vracet hodnotu.|  
|`Function`|Volitelné, ale buď `Sub` nebo `Function` musí být uvedena. Označuje, že externí procedura, vrátí hodnotu.|  
|`name`|Povinný parametr. Název externího odkazu. Další informace najdete v tématu [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Lib`|Povinný parametr. Zavádí `Lib` klauzuli, která identifikuje externí soubor (knihovna DLL nebo prostředek kódu) obsahující externí proceduru.|  
|`libname`|Povinný parametr. Název souboru, který obsahuje postup deklarovaný.|  
|`Alias`|Volitelné. Označuje, že název zadaný v nelze postup deklarované v rámci svého souboru identifikovat `name`. Zadejte jeho identifikaci v `aliasname`.|  
|`aliasname`|Povinné, pokud používáte `Alias` – klíčové slovo. Řetězec, který identifikuje postupu v jednom ze dvou způsobů:<br /><br /> Název vstupního bodu procedury v rámci svého souboru do uvozovek (`""`)<br /><br /> -nebo-<br /><br /> Znak čísla (`#`) následované celé číslo určující řadová číslovka vstupní bod podle postupu v jeho souboru|  
|`parameterlist`|Povinné, pokud, které procedura používá parametry. Zobrazit [seznam parametrů](../../../visual-basic/language-reference/statements/parameter-list.md).|  
|`returntype`|Požadováno pokud `Function` určena a `Option Strict` je `On`. Datový typ hodnoty vrácené procedurou.|  
  
## <a name="remarks"></a>Poznámky  
 Někdy potřebujete volání procedury definované v souboru (například DLL nebo prostředek) vně vašeho projektu. Když toto provedete, kompilátor jazyka Visual Basic nemá přístup k informacím, které potřebuje k voláním procedury správně, třeba kde je umístěn postup, jak je identifikovaný, jeho volací sekvence a návratový typ a řetězec znakové sady, které používá. `Declare` Příkaz vytvoří odkaz na externí procedura a poskytuje tyto nezbytné informace.  
  
 Můžete použít `Declare` pouze na úrovni modulu. To znamená, že *kontext deklarace* externího odkazu musí být třída, struktura nebo modulu a nemůže být zdrojový soubor, obor názvů, rozhraní, procedura nebo blok. Další informace najdete v tématu [kontexty deklarace a výchozí úrovně přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Externí odkazuje na výchozí [veřejné](../../../visual-basic/language-reference/modifiers/public.md) přístup. Můžete nastavit jejich úrovně přístupu modifikátory přístupu.  
  
## <a name="rules"></a>pravidla  
  
-   **Atributy.** Můžete použít atributy k externí odkaz. Všechny atributy, které použijete nemá vliv, pouze ve vašem projektu, ne v externím souboru.  
  
-   **Modifikátory.** Externí procedury jsou implicitně [Shared](../../../visual-basic/language-reference/modifiers/shared.md). Nelze použít `Shared` – klíčové slovo deklarace externí odkaz a nelze změnit stav jeho sdílení.  
  
     Externí procedura nemůže účastnit přepsání, implementovat členy rozhraní nebo zpracování událostí. Proto nelze použít `Overrides`, `Overridable`, `NotOverridable`, `MustOverride`, `Implements`, nebo `Handles` – klíčové slovo v `Declare` příkazu.  
  
-   **Název externí procedury.** Není nutné poskytnout tento vnější odkaz se stejným názvem (v `name`) jako název vstupního bodu podle postupu v jeho externí soubor (`aliasname`). Můžete použít `Alias` klauzule zadat název vstupního bodu. To může být užitečné v případě, že externí procedura má stejný název jako vyhrazené modifikátor jazyka Visual Basic nebo proměnné, procedura nebo jiné programovací element ve stejném oboru.  
  
    > [!NOTE]
    >  Názvy vstupního bodu ve většině knihoven DLL jsou malá a velká písmena.  
  
-   **Externí procedura číslo.** Alternativně můžete použít `Alias` klauzule k určení řadová číslovka vstupní bod v exportní tabulce externího souboru. K tomuto účelu začnete `aliasname` znakem čísla (`#`). To může být užitečné, pokud libovolný znak v názvu externí procedura není povolený v jazyce Visual Basic nebo na externí soubor exportuje postupu bez názvu.  
  
## <a name="data-type-rules"></a>Datový typ pravidla  
  
-   **Datové typy parametrů.** Pokud `Option Strict` je `On`, musíte zadat typ dat každého parametru ve `parameterlist`. To může být libovolného datového typu nebo název výčtu, strukturu, třídu nebo rozhraní. V rámci `parameterlist`, můžete použít `As` klauzule zadejte datový typ argumentu pro každý parametr předat.  
  
    > [!NOTE]
    >  V případě, že externí procedura nebyl zapsán pro rozhraní .NET Framework, je třeba Ujistěte se, že datové typy, které odpovídají. Například, pokud deklarujete externí odkaz na proceduru Visual Basic 6.0 se `Integer` parametr (16 bitů v jazyce Visual Basic 6.0), je nutné určit, odpovídající argument jako `Short` v `Declare` příkaz, protože to je 16 - v jazyce Visual Basic bit celočíselného typu. Obdobně `Long` má odlišnou datovou šířku v jazyce Visual Basic 6.0 a `Date` je implementováno jinak.  
  
-   **Návratový typ Data.** Je-li externí procedura `Function` a `Option Strict` je `On`, musíte zadat datový typ hodnoty vrácené volajícímu kódu. To může být libovolného datového typu nebo název výčtu, strukturu, třídu nebo rozhraní.  
  
    > [!NOTE]
    >  Kompilátor jazyka Visual Basic neověřuje, že datové typy jsou nekompatibilní s direktivami externí proceduru. Pokud dojde k neshodě, generuje modul common language runtime <xref:System.Runtime.InteropServices.MarshalDirectiveException> výjimka za běhu.  
  
-   **Výchozí datové typy.** Pokud `Option Strict` je `Off` a nezadáte datový typ parametru `parameterlist`, kompilátor jazyka Visual Basic převede odpovídající argument [datový typ objektu](../../../visual-basic/language-reference/data-types/object-data-type.md). Podobně pokud nezadáte `returntype`, kompilátor má návratový typ dat bude `Object`.  
  
    > [!NOTE]
    >  Vzhledem k tomu, že pracujete s externí procedura, která může být napsána na různé platformy, je nebezpečné, nevyvozujte předpoklady o datových typech a zajistí, aby výchozí. Je mnohem bezpečnější zadejte datový typ každý parametr nebo návratovou hodnotu, pokud existuje. To také zlepšuje čitelnost vašeho kódu.  
  
## <a name="behavior"></a>Chování  
  
-   **Obor.** Externí odkaz je v oboru v celém jeho třídy, struktury nebo modulu.  
  
-   **Doba platnosti.** Externí odkaz má stejnou dobu platnosti jako třídy, struktury nebo modul, ve kterém je deklarována.  
  
-   **Volání externí procedury.** Volání externí procedury stejně jako voláte `Function` nebo `Sub` proceduru – s použitím ve výrazech, pokud vrátí hodnotu, nebo zadáním v [volání příkazu](../../../visual-basic/language-reference/statements/call-statement.md) Pokud nevrací hodnotu.  
  
     Předání argumentů do externí procedury přesně podle specifikace `parameterlist` v `Declare` příkazu. Není vezměte v úvahu jak parametry byly původně deklarovány v externím souboru. Podobně, pokud je návratová hodnota, použít ho přesně podle specifikace `returntype` v `Declare` příkazu.  
  
-   **Znakové sady.** Můžete zadat v `charsetmodifier` jak by měl Visual Basic zařazovat řetězce při volání externí proceduru. `Ansi` Modifikátor instruuje Visual Basic zařazovat všechny řetězce na hodnoty ANSI a `Unicode` modifikátor přesměruje ho zařazovat všechny řetězce k hodnotám Unicode. `Auto` Modifikátor instruuje Visual Basic k zařazování řetězců v kódu podle rozhraní .NET Framework pravidla podle externího odkazu `name`, nebo `aliasname` -li zadán. Výchozí hodnota je `Ansi`.  
  
     `charsetmodifier` také určuje, jak by měl Visual Basic vyhledávat externí procedura v rámci svého externího souboru. `Ansi` a `Unicode` i přímé jazyka Visual Basic k vyhledání bez úpravy jejího názvu během vyhledávání. `Auto` instruuje Visual Basic k určení základní znakové sadě běhovou platformu a případně upravit název externí procedury následujícím způsobem:  
  
    -   Na platformě ANSI, například Windows 95, Windows 98 či Windows Millennium Edition nejdřív vyhledejte externí procedura bez úprav název. Pokud se to nepodaří, připojte na konec název externí procedury "A" a znovu vyhledat.  
  
    -   Na platformě Unicode, jako je například Windows NT, Windows 2000 nebo Windows XP nejprve vyhledejte externí procedura bez úprav název. Pokud se to nepodaří připojit "W" na konci externí procedura pojmenujte a znovu vyhledat.  
  
-   **Mechanismus.** Jazyk Visual Basic používá rozhraní .NET Framework *vyvolání platformy* (PInvoke) mechanismus řešení a přístup k externí procedury. `Declare` Příkazu a <xref:System.Runtime.InteropServices.DllImportAttribute> třída oba použít tento mechanismus automaticky a není nutné žádnou znalost PInvoke. Další informace najdete v tématu [názorný postup: Volání rozhraní API Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md).  
  
> [!IMPORTANT]
>  V případě, že externí procedura běží mimo modul CLR (CLR), je *nespravovaný kód*. Při volání tento postup, například funkce rozhraní Win32 API nebo metodu modelu COM může zveřejnit aplikaci na bezpečnostní rizika. Další informace najdete v tématu [zabezpečené kódování pokyny pro nespravovaný kód](../../../framework/security/secure-coding-guidelines-for-unmanaged-code.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad deklaruje externí odkaz na `Function` proceduru, která vrací aktuální uživatelské jméno. Potom volá externí procedura `GetUserNameA` jako součást `getUser` postup.  
  
 [!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]  
  
## <a name="example"></a>Příklad  
 <xref:System.Runtime.InteropServices.DllImportAttribute> Poskytuje alternativní způsob použití funkcí v nespravovaném kódu. Následující příklad deklaruje importované funkce bez použití `Declare` příkazu.  
  
 [!code-vb[VbVbalrStatements#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#16)]  
  
 [!code-vb[VbVbalrStatements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>
- [Příkaz Imports (obor názvů a typ .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Operátor AddressOf](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)
- [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Seznam parametrů](../../../visual-basic/language-reference/statements/parameter-list.md)
- [Příkaz Call](../../../visual-basic/language-reference/statements/call-statement.md)
- [Návod: Volání rozhraní API systému Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
