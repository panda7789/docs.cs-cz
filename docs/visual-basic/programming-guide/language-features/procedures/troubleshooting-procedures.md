---
title: Řešení potíží s procedurami (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting Visual Basic, procedures
- procedures [Visual Basic], troubleshooting
- Visual Basic code, procedures
- troubleshooting procedures
- procedures [Visual Basic], about procedures
ms.assetid: 525721e8-2e02-4f75-b5d8-6b893462cf2b
ms.openlocfilehash: f66e7f7444f2d3b1bb58bae6008f8896c81c2f76
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655516"
---
# <a name="troubleshooting-procedures-visual-basic"></a>Řešení potíží s procedurami (Visual Basic)
Tato stránka obsahuje některé běžné problémy, ke kterým dochází při práci s postupy.  
  
## <a name="returning-an-array-type-from-a-function-procedure"></a>Vrací typ pole z procedury – funkce  
 Pokud `Function` postup vrátí datového typu pole, nelze použít `Function` název pro uložení hodnot v elementech pole. Pokud se pokusíte k tomu, kompilátor ji interpretuje jako volání `Function`. Následující příklad generuje chyby kompilátoru.  
  
 `Function allOnes(ByVal n As Integer) As Integer()`  
  
 `For i As Integer = 1 To n - 1`  
  
 `' The following statement generates a`   `COMPILER ERROR`  `.`  
  
 `allOnes(i) = 1`  
  
 `Next i`  
  
 `' The following statement generates a`   `COMPILER ERROR`  `.`  
  
 `Return allOnes()`  
  
 `End Function`  
  
 Příkaz `allOnes(i) = 1` vygeneruje Chyba kompilátoru, protože se zdá, že volání `allOnes` s chybným datovým typem argument (jednotlivý prvek `Integer` místo `Integer` pole). Příkaz `Return allOnes()` vygeneruje Chyba kompilátoru, protože se zdá, že volání `allOnes` s žádný argument.  
  
 **Správný způsob:** mohli upravit prvky pole, které se vrátí, definovat interní pole jako místní proměnné. V následujícím příkladu se zkompiluje bez chyby.  
  
 [!code-vb[VbVbcnProcedures#66](./codesnippet/VisualBasic/troubleshooting-procedures_1.vb)]  
  
## <a name="argument-not-being-modified-by-procedure-call"></a>Argument není upravována voláním procedury  
 Pokud máte v úmyslu povolit postup, chcete-li změnit programovací element základní argument ve volání kódu, musí se splnit odkazem. Ale procedury přístup i v případě, že jí předáte hodnotu elementy argument typu odkaz.  
  
-   **Základní proměnné**. Povolit postup nahraďte hodnotu základní proměnné elementu samotného, musí deklarovat postup parametr [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md). Navíc volající kód nesmí uzavřete jej v závorkách, vzhledem k tomu, který by se mělo přepsat `ByRef` předávání mechanismus.  
  
-   **Referenční elementy typu**. Pokud je parametr deklarovat [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md), postup nelze upravit základní proměnné elementu samotného. Ale pokud argument typu odkazu, postup můžete upravit členy objektu, na kterou odkazuje, i když ho nelze nahradit hodnota proměnné. Například pokud je argumentem proměnná typu pole, postup nelze přiřadit nové pole do ní, ale můžete změnit, nejméně jeden z jejích elementů. Změněné elementy se projeví v podkladové proměnné pole v volající kód.  
  
 V následujícím příkladu definuje dva postupy, které provádějí proměnné pole podle hodnoty a pracovat na jeho elementy. Postup `increase` jednoduše přidá jeden na každý element. Postup `replace` přiřadí nové pole do parametru `a()` a potom přidá jeden na každý element. Však opětovné přiřazení neovlivňuje základní proměnné pole v kód volání, protože `a()` je deklarovaná `ByVal`.  
  
 [!code-vb[VbVbcnProcedures#35](./codesnippet/VisualBasic/troubleshooting-procedures_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#38](./codesnippet/VisualBasic/troubleshooting-procedures_3.vb)]  
  
 Následující příklad provádí volání na `increase` a `replace`.  
  
 [!code-vb[VbVbcnProcedures#37](./codesnippet/VisualBasic/troubleshooting-procedures_4.vb)]  
  
 První `MsgBox` volání zobrazí "po increase(n): 11, 21, 31, 41". Protože `n` je typu odkazu `increase` můžete změnit její členy, i když je předán `ByVal`.  
  
 Druhý `MsgBox` volání zobrazí "po replace(n): 11, 21, 31, 41". Protože `n` je předán `ByVal`, `replace` nelze upravit proměnnou `n` přiřazením nové pole. Když `replace` vytvoří novou instanci pole `k` a přiřadí ji k místní proměnné `a`, se ztratí odkaz na `n` předaná volající kódem. Když se zvýší členů `a`, pouze místní pole `k` má vliv.  
  
 **Správný způsob:** mohli upravit základní proměnné elementu samotného, předání odkazem. Následující příklad ukazuje změnu v deklaraci `replace` umožňuje jej nahradit jiným v kód volání jedno pole.  
  
 [!code-vb[VbVbcnProcedures#64](./codesnippet/VisualBasic/troubleshooting-procedures_5.vb)]  
  
## <a name="unable-to-define-an-overload"></a>Nelze definovat přetížení  
 Pokud chcete definovat přetížené verzi postup, musíte použít stejný název, ale jiný podpis. Pokud kompilátor nelze rozlišit vaší deklaraci ze přetížení se stejným podpisem, vygeneruje se chyba.  
  
 *Podpis* procedury je dáno tím název procedury a seznam parametrů. Každé přetížení musí mít stejný název jako všechny ostatní přetížení ale se musí lišit od všech těchto alespoň v jedné další komponenty podpis. Další informace najdete v tématu [přetížení procedury](./procedure-overloading.md).  
  
 Následující položky, i když se týkají do seznamu parametrů nejsou součástí podpisu postup:  
  
-   Postup modifikátor klíčová slova, jako například `Public`, `Shared`, a `Static`  
  
-   Názvy parametrů  
  
-   Klíčová slova – modifikátor parametrů, jako například `ByRef` a `Optional`  
  
-   datový typ vrácené hodnoty (s výjimkou operátora převodu)  
  
 Pomocí různých pouze jeden nebo více předchozí položky nelze přetížení procedury.  
  
 **Správný způsob:** mohli definovat přetížení procedury, musí být podpis. Protože je nutné použít stejný název, musí se liší čísla, pořadí nebo datové typy parametrů. Obecný postup můžete měnit počet parametrů typu. V operátora převodu ([CType – funkce](../../../../visual-basic/language-reference/functions/ctype-function.md)), návratový typ se může lišit.  
  
### <a name="overload-resolution-with-optional-and-paramarray-arguments"></a>Přetížení řešení s volitelné a ParamArray – argumenty  
 Pokud jsou přetížení procedury s jedním nebo více [volitelné](../../../../visual-basic/language-reference/modifiers/optional.md) parametry nebo [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parametr, je nutné se neduplikovaly některé z *implicitní přetížení*. Informace najdete v tématu [aspekty přetížení procedur](./considerations-in-overloading-procedures.md).  
  
## <a name="calling-a-wrong-version-of-an-overloaded-procedure"></a>Volání nesprávný verzi přetížené procedury  
 Pokud procedury má několik přetížené verzí, by měl být obeznámeni s jejich seznamy parametrů a pochopit, jak Visual Basic přeloží volání mezi přetížení. V opačném případě může volat přetížení než zamýšlené.  
  
 Pokud zjistíte, které přetížení, které chcete volat, pečlivě dodržujte přitom následující pravidla:  
  
-   Zadejte správný počet argumentů a ve správném pořadí.  
  
-   V ideálním případě by měli vaší argumenty přesně stejnou typy dat, jako odpovídající parametry. Datový typ jednotlivých argumentu musí v žádném případě rozšíří do u jeho odpovídající parametr. To platí to i [Option Strict – příkaz](../../../../visual-basic/language-reference/statements/option-strict-statement.md) nastavena na `Off`. Pokud přetížení vyžaduje, aby všechny zužující převod ze seznamu argument, který přetížení nejsou způsobilé k volání.  
  
-   Pokud zadáte argumenty, které vyžadují rozšíření, zkontrolujte své datové typy jak nejblíže k odpovídající datové typy parametrů. Pokud dva nebo více přetížení přijmout svým datovým typům argument, kompilátor přeloží volání přetížení, které žádá minimem rozšíření.  
  
 Můžete snížit riziko neshody typu dat pomocí [CType – funkce](../../../../visual-basic/language-reference/functions/ctype-function.md) – klíčové slovo převodu při přípravě vašeho argumenty.  
  
### <a name="overload-resolution-failure"></a>Chybě rozlišení přetížení  
 Při volání přetížené procedury, pokusí se kompilátor odstranit všechny kromě jednoho z přetížení. Pokud se aktivace podaří, přeloží volání této přetížení. Pokud eliminuje všechny přetížení, nebo ho nelze zmenšit oprávněné přetížení do jediného kandidáta, vygeneruje se chyba.  
  
 Následující příklad znázorňuje proces rozlišení přetížení.  
  
 [!code-vb[VbVbcnProcedures#62](./codesnippet/VisualBasic/troubleshooting-procedures_6.vb)]  
  
 [!code-vb[VbVbcnProcedures#63](./codesnippet/VisualBasic/troubleshooting-procedures_7.vb)]  
  
 Při prvním volání do kompilátoru eliminuje první přetížení, protože typ prvního argumentu (`Short`) zmenší tak, aby typ odpovídající parametru (`Byte`). Protože každý argument typ v druhé přetížení pak eliminuje třetí přetížení (`Short` a `Single`) rozšiřuje odpovídající typ v třetí přetížení (`Integer` a `Single`). Druhý přetížení vyžaduje méně rozšíření, kompilátor použije pro volání.  
  
 V druhé volání do kompilátoru nelze eliminovat žádné přetížení na základě zužující. Eliminuje třetí přetížení ze stejného důvodu jako první volání, protože ji můžete volat druhý přetížení s menší rozšiřující s typy argumentů. Kompilátor však nelze vyřešit mezi prvním a druhém přetížení. Každá z nich má jeden typ definované parametru, která rozšiřuje odpovídající typ v dalších (`Byte` k `Short`, ale `Single` k `Double`). Kompilátor proto vygeneruje chybu rozlišení přetížení.  
  
 **Správný způsob:** Pokud chcete mít možnost volání přetížené procedury bez nejednoznačnost, použijte [CType – funkce](../../../../visual-basic/language-reference/functions/ctype-function.md) tak, aby odpovídaly argument datové typy pro typy parametrů. Následující příklad ukazuje volání `z` který vynutí řešení druhý přetížení.  
  
 [!code-vb[VbVbcnProcedures#65](./codesnippet/VisualBasic/troubleshooting-procedures_8.vb)]  
  
### <a name="overload-resolution-with-optional-and-paramarray-arguments"></a>Přetížení řešení s volitelné a ParamArray – argumenty  
 Pokud dva přetížení procedury mít identické podpisy s tím rozdílem, že je deklarovaná poslední parametr [volitelné](../../../../visual-basic/language-reference/modifiers/optional.md) v jednom a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) do druhé kompilátor přeloží volání této procedury podle nejblíže shoda. Další informace najdete v tématu [rozlišení přetížení](./overload-resolution.md).  
  
## <a name="see-also"></a>Viz také  
 [Procedury](./index.md)  
 [Procedury Sub](./sub-procedures.md)  
 [Procedury funkce](./function-procedures.md)  
 [Procedury vlastnosti](./property-procedures.md)  
 [Procedury operátoru](./operator-procedures.md)  
 [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)  
 [Přetížení procedury](./procedure-overloading.md)  
 [Aspekty přetížení procedur](./considerations-in-overloading-procedures.md)  
 [Řešení přetížení](./overload-resolution.md)
