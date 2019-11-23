---
title: Postupy řešení potíží (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting Visual Basic, procedures
- procedures [Visual Basic], troubleshooting
- Visual Basic code, procedures
- troubleshooting procedures
- procedures [Visual Basic], about procedures
ms.assetid: 525721e8-2e02-4f75-b5d8-6b893462cf2b
ms.openlocfilehash: c74947e21de8ba26ffde01f6f28aea67346c2071
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002074"
---
# <a name="troubleshooting-procedures-visual-basic"></a>Postupy řešení potíží (Visual Basic)

Tato stránka obsahuje některé běžné problémy, které mohou nastat při práci s postupy.  
  
## <a name="returning-an-array-type-from-a-function-procedure"></a>Vrácení typu pole z procedury funkce

Pokud `Function` procedura vrátí datový typ pole, nelze použít `Function` název k uložení hodnot do prvků pole. Pokud se o to pokusíte, kompilátor ho interpretuje jako volání `Function`. Následující příklad generuje chyby kompilátoru:
  
```vb
Function AllOnes(n As Integer) As Integer()
   For i As Integer = 1 To n - 1  
      ' The following statement generates a COMPILER ERROR.  
      AllOnes(i) = 1  
   Next  

   ' The following statement generates a COMPILER ERROR.  
   Return AllOnes()  
End Function
```

Příkaz `AllOnes(i) = 1` vygeneruje chybu kompilátoru, protože se zobrazí volání `AllOnes` s argumentem nesprávného datového typu (skalární `Integer` místo pole `Integer`). Příkaz `Return AllOnes()` vygeneruje chybu kompilátoru, protože se zobrazí volání `AllOnes` bez argumentu.  
  
 **Správný přístup:** Aby bylo možné upravit prvky pole, které má být vráceno, definujte interní pole jako místní proměnnou. Následující příklad zkompiluje bez chyby:

 [!code-vb[VbVbcnProcedures#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#66)]

## <a name="argument-not-modified-by-procedure-call"></a>Argument nebyl pozměněn voláním procedury.

Pokud máte v úmyslu, aby bylo možné změnit programovací prvek podkladovým argumentem v volajícím kódu, je nutné jej předat odkazem. Ale procedura má přístup k prvkům argumentu typu odkazu, i když ho předáte hodnotou.

- **Podkladová proměnná**. Chcete-li dovolit, aby procedura nahradila hodnotu samotného základního prvku proměnné, procedura musí deklarovat parametr [ByRef](../../../language-reference/modifiers/byref.md). Kromě toho volající kód nesmí uzavřít argument do závorek, protože by došlo k přepsání mechanismu předávání `ByRef`.

- **Prvky typu odkazu**. Pokud deklarujete parametr [ByVal](../../../language-reference/modifiers/byval.md), procedura nemůže změnit samotný nadřízený prvek proměnné. Nicméně pokud je argumentem odkazový typ, procedura může změnit členy objektu, na který odkazuje, i když nemůže nahradit hodnotu proměnné. Například pokud je argumentem proměnná pole, procedura k ní nemůže přiřadit nové pole, ale může změnit jeden nebo více jeho prvků. Změněné prvky se projeví v podkladové proměnné pole v kódu volání.

Následující příklad definuje dva postupy, které přebírají proměnnou pole podle hodnoty a pracují s jejími prvky. Procedura `increase` jednoduše přidá jeden do každého prvku. Procedura `replace` přiřadí k parametru nové pole `a()` a poté přidá jeden do každého prvku. Opětovné přiřazení však nemá vliv na podkladovou proměnnou pole v kódu volání, protože `a()` je deklarována `ByVal`.

[!code-vb[VbVbcnProcedures#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#35)]

[!code-vb[VbVbcnProcedures#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#38)]

Následující příklad provede volání `increase` a `replace`:

[!code-vb[VbVbcnProcedures#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#37)]
  
První `MsgBox` volání zobrazí "po zvýšení (n): 11, 21, 31, 41". Vzhledem k tomu, že `n` je odkazový typ, `increase` může změnit jeho členy, i když je předáno `ByVal`.

Druhý `MsgBox` volání zobrazí "po nahrazení (n): 11, 21, 31, 41". Vzhledem k tomu, že `n` předává `ByVal`, `replace` nemůže změnit proměnnou `n` přiřazením nového pole. Když `replace` vytvoří novou instanci pole `k` a přiřadí ji k lokální proměnné `a`, ztratí odkaz na `n` předaný volajícím kódem. Když dojde ke zvýšení počtu členů `a`, bude ovlivněn pouze místní pole `k`.

**Správný přístup:** Aby bylo možné upravovat základní prvek proměnné, předejte ho odkazem. Následující příklad ukazuje změnu v deklaraci `replace`, která umožňuje nahradit jedno pole jiným v kódu volání:

[!code-vb[VbVbcnProcedures#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#64)]

## <a name="unable-to-define-an-overload"></a>Nejde definovat přetížení.

Pokud chcete definovat přetíženou verzi procedury, je nutné použít stejný název, ale jiný podpis. Pokud kompilátor nemůže odlišit vaši deklaraci od přetížení se stejnou signaturou, vygeneruje chybu.

*Signatura* procedury je určena názvem procedury a seznamem parametrů. Každé přetížení musí mít stejný název jako všechna ostatní přetížení, ale musí se lišit od všech z nich alespoň v jedné z ostatních součástí signatury. Další informace najdete v tématu [přetížení procedury](./procedure-overloading.md).

Následující položky, i když se vztahují k seznamu parametrů, nejsou součástí signatury procedury:

- Klíčová slova modifikátoru procedury, například `Public`, `Shared`a `Static`.
- Názvy parametrů
- Klíčová slova modifikátoru parametru, například `ByRef` a `Optional`.
- Datový typ návratové hodnoty (s výjimkou operátoru převodu).

Nemůžete přetížit proceduru změnou pouze jedné nebo více předchozích položek.

**Správný přístup:** Aby bylo možné definovat přetížení procedury, je nutné změnit signaturu. Vzhledem k tomu, že je nutné použít stejný název, je nutné změnit počet, pořadí nebo datové typy parametrů. V obecné proceduře můžete změnit počet parametrů typu. V operátoru převodu ([funkce CType](../../../language-reference/functions/ctype-function.md)) můžete změnit návratový typ.

### <a name="overload-resolution-with-optional-and-paramarray-arguments"></a>Rozlišení přetěžování pomocí volitelných argumentů a argumentů ParamArray

Pokud přetěžujete proceduru s jedním nebo více [volitelnými](../../../language-reference/modifiers/optional.md) parametry nebo parametrem [ParamArray](../../../language-reference/modifiers/paramarray.md) , je nutné se vyhnout duplikování jakýchkoli *implicitních přetížení*. Informace najdete v tématu věnovaném [důležitým postupům při přetížení](./considerations-in-overloading-procedures.md).

## <a name="calling-the-wrong-version-of-an-overloaded-procedure"></a>Volání nesprávné verze přetížené procedury

Pokud má procedura několik přetížených verzí, měli byste být obeznámeni se všemi jejich seznamy parametrů a porozumět tomu, jak Visual Basic řeší volání mezi přetíženími. V opačném případě můžete volat přetížení jiné než zamýšlené.

Když určíte, které přetížení chcete volat, buďte opatrní, abyste zjistili následující pravidla:

- Zadejte správný počet argumentů a ve správném pořadí.  
- V ideálním případě by měly mít vaše argumenty stejné typy dat jako odpovídající parametry. V každém případě se musí datový typ každého argumentu rozšířit na příslušný parametr. To platí i s [příkazem Option Strict](../../../language-reference/statements/option-strict-statement.md) nastaveným na `Off`. Pokud přetížení vyžaduje jakýkoliv zužující převod ze seznamu argumentů, není možné volat přetížení.
- Pokud zadáte argumenty, které vyžadují rozšiřování, zpřístupněte jejich datové typy co nejblíže odpovídajícím datovým typům parametrů. Pokud dva nebo více přetížení akceptuje datové typy argumentů, kompilátor vyřeší volání přetížení, které volá pro nejmenší množství rozšiřování.

Při přípravě argumentů můžete snížit pravděpodobnost neshody datových typů pomocí klíčového slova konverze [funkce CType](../../../language-reference/functions/ctype-function.md) .

### <a name="overload-resolution-failure"></a>Selhání Rozlišení přetěžování

Při volání přetížené procedury se kompilátor pokusí odstranit všechny, ale jedno z přetížení. Pokud bude úspěšná, vyřeší volání tohoto přetížení. Pokud se eliminují všechna přetížení, nebo pokud nemůže snížit nárokná přetížení na jednoho kandidáta, vygeneruje chybu.

Následující příklad znázorňuje proces řešení přetížení:

[!code-vb[VbVbcnProcedures#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#62)]

[!code-vb[VbVbcnProcedures#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#63)]
  
Při prvním volání kompilátor eliminuje první přetížení, protože typ prvního argumentu (`Short`) se zúží na typ odpovídajícího parametru (`Byte`). Pak eliminuje třetí přetížení, protože každý argument typu v druhém přetížení (`Short` a `Single`) se rozšíří na odpovídající typ třetí přetížení (`Integer` a `Single`). Druhé přetížení vyžaduje méně rozšiřování, takže ho kompilátor použije pro volání.

Ve druhém volání kompilátor nemůže eliminovat žádné přetížení na základě zúžení. Vylučuje třetí přetížení pro stejný důvod jako v prvním volání, protože může zavolat druhé přetížení s menším rozšiřováním typů argumentů. Kompilátor však nemůže vyřešit mezi prvním a druhým přetížením. Každý má jeden definovaný typ parametru, který se rozšíří na odpovídající typ v druhé (`Byte` pro `Short`, ale `Single` na `Double`). Kompilátor proto vygeneruje chybu rozlišení přetížení.

**Správný přístup:** Aby bylo možné volat přetíženou proceduru bez nejednoznačnosti, použijte [funkci CType](../../../language-reference/functions/ctype-function.md) , která bude odpovídat datovým typům argumentu na typy parametrů. Následující příklad ukazuje volání `z`, které vynucuje řešení druhého přetížení.

[!code-vb[VbVbcnProcedures#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#65)]

### <a name="overload-resolution-with-optional-and-paramarray-arguments"></a>Rozlišení přetěžování pomocí volitelných argumentů a argumentů ParamArray

Pokud dvě přetížení procedury mají stejné signatury s tím rozdílem, že poslední parametr je deklarován jako [volitelné](../../../language-reference/modifiers/optional.md) v jednom a [ParamArray](../../../language-reference/modifiers/paramarray.md) v druhé, kompilátor vyřeší volání této procedury podle nejbližší shody. Další informace najdete v tématu [řešení přetížení](./overload-resolution.md).

## <a name="see-also"></a>Viz také:

- [Procedury](index.md)
- [Procedury Sub](sub-procedures.md)
- [Procedury funkce](function-procedures.md)
- [Procedury vlastnosti](property-procedures.md)
- [Procedury operátoru](operator-procedures.md)
- [Parametry a argumenty procedury](procedure-parameters-and-arguments.md)
- [Přetížení procedury](procedure-overloading.md)
- [Aspekty přetížení procedur](considerations-in-overloading-procedures.md)
- [Řešení přetížení](overload-resolution.md)
