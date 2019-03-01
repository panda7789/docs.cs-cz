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
ms.openlocfilehash: e29e4a3b216657b398407701530ad9bfe975dbf6
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56971998"
---
# <a name="troubleshooting-procedures-visual-basic"></a>Řešení potíží s procedurami (Visual Basic)
Tato stránka obsahuje některé běžné problémy, které se mohou vyskytnout při práci s postupy.  
  
## <a name="returning-an-array-type-from-a-function-procedure"></a>Vrací typ pole z procedury – funkce  
 Pokud `Function` procedura vrací datový typ pole, nelze použít `Function` název pro ukládání hodnot prvků pole. Pokud se pokusíte k tomu, kompilátor ji interpretuje jako volání `Function`. Následující příklad generuje chyby kompilátoru.  
  
 `Function allOnes(ByVal n As Integer) As Integer()`  
  
 `For i As Integer = 1 To n - 1`  
  
 `' The following statement generates a`   `COMPILER ERROR`  `.`  
  
 `allOnes(i) = 1`  
  
 `Next i`  
  
 `' The following statement generates a`   `COMPILER ERROR`  `.`  
  
 `Return allOnes()`  
  
 `End Function`  
  
 Příkaz `allOnes(i) = 1` vygeneruje chybu kompilátoru, protože to vypadá, volání `allOnes` s argumentem typu chybná data (jednotlivý prvek `Integer` místo `Integer` pole). Příkaz `Return allOnes()` vygeneruje chybu kompilátoru, protože to vypadá, volání `allOnes` s žádný argument.  
  
 **Správný způsob:** Aby bylo možné upravit prvky pole, které má být vrácena, definujte interní pole jako místní proměnná. Následující příklad se zkompiluje bez chyb.  
  
 [!code-vb[VbVbcnProcedures#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#66)]  
  
## <a name="argument-not-being-modified-by-procedure-call"></a>Argument není právě upravuje voláním procedury  
 Pokud chcete povolit postup, chcete-li změnit programovací element základní argumentu ve volajícím kódu, musíte jí předat podle odkazu. Ale postup může přistupovat k prvkům argument typu odkazu, i v případě, předat podle hodnoty.  
  
-   **Základní proměnná**. Povolit postup k nahrazení hodnoty základní proměnné elementu samotného, procedura musí deklarovat parametr [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md). Navíc volající kód nesmí uvést argument v závorkách, protože, který by se mělo přepsat `ByRef` předávání mechanismus.  
  
-   **Odkazovat na prvky typu**. Pokud deklarujete parametr [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md), postup nelze změnit základní proměnné elementu samotného. Ale pokud je argumentem Typ odkazu, postupu můžete upravit členy objektu, na kterou odkazuje, i když ho nelze nahradit hodnotu proměnné. Například pokud má argument hodnotu proměnné pole, postup nelze přiřadit nové pole do ní, ale můžete změnit jednu nebo více z jeho prvků. Změněné prvky se projeví v základní proměnné pole ve volajícím kódu.  
  
 Následující příklad definuje dva postupy, které v této proměnné pole hodnota a provozují na jeho prvků. Postup `increase` jednoduše přidá jednu na každý prvek. Postup `replace` přiřadí nové pole parametru `a()` a pak přidá jednu na každý prvek. Ale přeřazení neovlivní základní proměnné pole ve volajícím kódu, protože `a()` je deklarován `ByVal`.  
  
 [!code-vb[VbVbcnProcedures#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#35)]  
  
 [!code-vb[VbVbcnProcedures#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#38)]  
  
 Následující příklad provede volání `increase` a `replace`.  
  
 [!code-vb[VbVbcnProcedures#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#37)]  
  
 První `MsgBox` volání zobrazí "po increase(n): 11, 21, 31, 41". Protože `n` je typem odkazu `increase` lze měnit její členy, i když je jí předán `ByVal`.  
  
 Druhá `MsgBox` volání zobrazí "po replace(n): 11, 21, 31, 41". Protože `n` je předán `ByVal`, `replace` nelze upravit proměnnou `n` přiřazením nového pole. Když `replace` vytvoří novou instanci pole `k` a přiřadí ji na místní proměnnou `a`, ztratí odkaz na `n` předaných v volající kód. Když zvýší členy `a`, pouze místní pole `k` má vliv.  
  
 **Správný způsob:** Abyste mohli upravovat základní prvek proměnné samotné, předávání odkazem. Následující příklad ukazuje změnu v deklaraci `replace` , který umožňuje jedno pole nahradit jiným ve volajícím kódu.  
  
 [!code-vb[VbVbcnProcedures#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#64)]  
  
## <a name="unable-to-define-an-overload"></a>Nelze definovat přetíženou  
 Pokud chcete definovat přetížené verze procedury, musíte použít stejný název, ale jiným podpisem. Pokud kompilátor nemůže rozlišit vaše deklarace z přetížení se stejným podpisem, dojde k chybě.  
  
 *Podpis* procedury je určen název procedury a seznamu parametrů. Jednotlivá přetížení, musí mít stejný název jako všechna přetížení ale se musí lišit od všechny z nich alespoň v jedné další komponenty podpisu. Další informace najdete v tématu [přetížení procedury](./procedure-overloading.md).  
  
 Následující položky, i v případě, že jde o jejich vztah k seznamu parametrů nejsou součástí podpis postupem:  
  
-   Postup modifikátor klíčová slova, jako například `Public`, `Shared`, a `Static`  
  
-   Názvy parametrů  
  
-   Klíčová slova modifikátor parametru, jako například `ByRef` a `Optional`  
  
-   Datový typ vrácené hodnoty (s výjimkou operátoru převodu)  
  
 Pomocí různých pouze jeden nebo více předchozích položek nelze přetížení procedury.  
  
 **Správný způsob:** Aby bylo možné definovat přetížení procedury, musí se liší podpis. Protože je nutné použít stejný název, musí se liší počet, pořadí nebo datové typy parametrů. V obecný postup je popsán můžete měnit počet parametrů typu. V operátoru převodu ([funkce CType](../../../../visual-basic/language-reference/functions/ctype-function.md)), návratový typ se může lišit.  
  
### <a name="overload-resolution-with-optional-and-paramarray-arguments"></a>Přetížení překlad IP adres s volitelným a ParamArray – argumenty  
 Pokud jsou přetížení procedury s jednou nebo více [volitelné](../../../../visual-basic/language-reference/modifiers/optional.md) parametry nebo [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parametr, je třeba se vyvarovat duplikování všech *implicitní přetížení*. Informace najdete v tématu [aspekty přetížení procedur](./considerations-in-overloading-procedures.md).  
  
## <a name="calling-a-wrong-version-of-an-overloaded-procedure"></a>Volání nesprávné verze třídy přetížené procedury  
 Pokud procedura má několik přetížené verze, by měl být obeznámeni s jejich seznamy parametrů a pochopit, jak Visual Basic přeloží volání mezi přetížení. Jinak lze volat přetížení než zamýšlené.  
  
 Pokud jste určili přetížení, které chcete volat, dejte pozor, dodržovat následující pravidla:  
  
-   Zadejte správný počet argumentů a ve správném pořadí.  
  
-   V ideálním případě by vaše argumenty by měly obsahovat přesně stejné datové typy jako odpovídající parametry. Datový typ každého argumentu musí v každém případě rozšířit na u jeho odpovídajícího parametru. To platí i v případě [Option Strict – příkaz](../../../../visual-basic/language-reference/statements/option-strict-statement.md) nastavena na `Off`. Pokud jakýkoli zužující převod seznam argumentů, které přetížení vyžaduje přetížení nemá oprávnění volat.  
  
-   Pokud zadáte argumenty, které vyžadují rozšíření, ujistěte se, co nejblíže k odpovídající datové typy parametrů jejich datové typy. Pokud dva nebo více přetížení přijmout vaší datové typy argumentů, kompilátor překládá volání přetížení, které vyžaduje minimální množství rozšíření.  
  
 Můžete snížit pravděpodobnost svého neshody typů dat pomocí [funkce CType](../../../../visual-basic/language-reference/functions/ctype-function.md) – klíčové slovo převodu při přípravě vaše argumenty.  
  
### <a name="overload-resolution-failure"></a>Chybě rozlišení přetížení  
 Při volání přetížené procedury, kompilátor se pokusí odstranit všechny kromě jednoho z přetížení. Pokud se aktivace podaří, přeloží volání tohoto přetížení. Pokud eliminuje všechna přetížení, nebo pokud ji nemůžete zmenšit oprávněné přetížení k jedné Release candidate, dojde k chybě.  
  
 Následující příklad znázorňuje proces řešení přetížení.  
  
 [!code-vb[VbVbcnProcedures#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#62)]  
  
 [!code-vb[VbVbcnProcedures#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#63)]  
  
 Při prvním volání, kompilátor eliminuje první přetížení, protože typ prvního argumentu (`Short`) zužuje na typ odpovídající parametru (`Byte`). Eliminuje pak třetí přetížení, protože typ každého argumentu ve druhé přetížení (`Short` a `Single`) rozšiřuje na odpovídající typ v třetí přetížení (`Integer` a `Single`). Druhé přetížení vyžaduje méně rozšíření, takže kompilátor používá volání.  
  
 V druhém volání nelze odstranit kompilátor některý z přetížení na základě zužující. Eliminuje třetí přetížení ze stejného důvodu jako první volání, vzhledem k tomu, že může volat druhé přetížení s méně rozšiřující typy argumentů. Kompilátor však nelze rozlišit mezi první a druhé přetížení. Každá má jeden typ definovaný parametr, který rozšiřuje na odpovídající typ v jiném (`Byte` k `Short`, ale `Single` k `Double`). Kompilátor tedy dojde k chybě rozlišení přetížení.  
  
 **Správný způsob:** Aby bylo možné volání přetížené procedury bez nejednoznačnost, použijte [funkce CType](../../../../visual-basic/language-reference/functions/ctype-function.md) tak, aby odpovídaly datové typy argumentů na typy parametrů. Následující příklad ukazuje volání `z` druhé přetížení, která vynutí řešení.  
  
 [!code-vb[VbVbcnProcedures#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#65)]  
  
### <a name="overload-resolution-with-optional-and-paramarray-arguments"></a>Přetížení překlad IP adres s volitelným a ParamArray – argumenty  
 Pokud dvě přetížení procedury, mají stejné podpisy, s tím rozdílem, že je deklarován poslední parametr [volitelné](../../../../visual-basic/language-reference/modifiers/optional.md) v jednom a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) , ve druhém přeloží kompilátor volání této procedury podle nejvíce odpovídá. Další informace najdete v tématu [rozlišení přetížení](./overload-resolution.md).  
  
## <a name="see-also"></a>Viz také:
- [Procedury](./index.md)
- [Procedury Sub](./sub-procedures.md)
- [Procedury funkce](./function-procedures.md)
- [Procedury vlastnosti](./property-procedures.md)
- [Procedury operátoru](./operator-procedures.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Přetížení procedury](./procedure-overloading.md)
- [Aspekty přetížení procedur](./considerations-in-overloading-procedures.md)
- [Řešení přetížení](./overload-resolution.md)
