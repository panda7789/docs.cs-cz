---
title: Deklarace proměnné
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], declaring
- member variables [Visual Basic], declarations
- Dim statement [Visual Basic], variable declaration
- declaring variables [Visual Basic]
- variables [Visual Basic], scope
- variables [Visual Basic], data types
- data types [Visual Basic], variable declarations
- lifetime [Visual Basic], variables
- variables [Visual Basic], lifetime
- access levels [Visual Basic], variables
- scope [Visual Basic], declaration statements
- variables [Visual Basic], access level
- local variables [Visual Basic], declarations
- scope [Visual Basic], variables
ms.assetid: d8f10226-92b1-480f-9f53-df377b2d7e15
ms.openlocfilehash: 587cb84faa09b686361c255c413ad852780b8971
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410293"
---
# <a name="variable-declaration-in-visual-basic"></a>Deklarace proměnné v jazyce Visual Basic
Deklarujete proměnnou pro určení jejího názvu a charakteristiky. Příkaz deklarace pro proměnné je [příkaz Dim](../../../language-reference/statements/dim-statement.md). Jeho umístění a obsah určují charakteristiky proměnné.  
  
 Informace o pravidlech pojmenovávání a požadavcích naleznete v tématu [deklarované názvy elementů](../declared-elements/declared-element-names.md).  
  
## <a name="declaration-levels"></a>Úrovně deklarací  
  
### <a name="local-and-member-variables"></a>Místní a členské proměnné  
 *Lokální proměnná* je jedna, která je deklarována v rámci procedury. *Členská proměnná* je členem Visual Basicho typu; je deklarována na úrovni modulu uvnitř třídy, struktury nebo modulu, ale ne v rámci žádné procedury vnitřní k této třídě, struktuře nebo modulu.  
  
### <a name="shared-and-instance-variables"></a>Sdílené a proměnné instance  
 Ve třídě nebo struktuře závisí kategorie členské proměnné na tom, zda je nebo není sdílena. Je-li deklarován se [sdíleným](../../../language-reference/modifiers/shared.md) klíčovým slovem, jedná se o *sdílenou proměnnou*a existuje v jedné kopii sdílené mezi všemi instancemi třídy nebo struktury.  
  
 V opačném případě se jedná o *proměnnou instance*a samostatná kopie je vytvořena pro každou instanci třídy nebo struktury. Daná kopie proměnné instance je k dispozici pouze pro instanci třídy nebo struktury, ve které byla vytvořena. Je nezávislý na kopii proměnné instance v jakékoli jiné instanci třídy nebo struktury.  
  
## <a name="declaring-data-type"></a>Deklarace datového typu  
 Klauzule [as](../../../language-reference/statements/as-clause.md) v příkazu Declaration umožňuje definovat datový typ nebo typ objektu pro proměnnou, kterou deklarujete. Pro proměnnou můžete zadat kterýkoli z následujících typů:  
  
- Základní datový typ, například `Boolean` , `Long` nebo`Decimal`  
  
- Složený datový typ, jako je například pole nebo struktura  
  
- Typ objektu nebo třída definovaný buď v aplikaci, nebo v jiné aplikaci.  
  
- .NET Framework třídy, například <xref:System.Windows.Forms.Label> nebo<xref:System.Windows.Forms.TextBox>  
  
- Typ rozhraní, například <xref:System.IComparable> nebo<xref:System.IDisposable>  
  
 Můžete deklarovat několik proměnných v jednom příkazu bez nutnosti opakovat datový typ. V následujících příkazech `i` jsou proměnné, `j` a `k` deklarovány jako typ `Integer` `l` a jako a `m` `Long` `x` a a `y` jako `Single` :  
  
```vb  
Dim i, j, k As Integer  
' All three variables in the preceding statement are declared as Integer.  
Dim l, m As Long, x, y As Single  
' In the preceding statement, l and m are Long, x and y are Single.  
```  
  
 Další informace o typech dat najdete v tématu [datové typy](../data-types/index.md). Další informace o objektech naleznete v tématu [objekty a třídy](../objects-and-classes/index.md) a [programování pomocí komponent](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0ffkdtkf(v=vs.120)).  
  
## <a name="local-type-inference"></a>Odvození místního typu  
 *Odvození typu* se používá k určení datových typů místních proměnných deklarovaných bez `As` klauzule. Kompilátor odvodí typ proměnné z typu inicializačního výrazu. To umožňuje deklarovat proměnné bez explicitního oznámení typu. V následujícím příkladu `num1` a `num2` jsou silného typu jako celá čísla.  
  
 [!code-vb[VbVbalrTypeInference#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#1)]  
  
 Pokud chcete použít odvození místního typu, `Option Infer` musí být nastavena na `On` . Další informace naleznete v tématu [odvození místního typu](local-type-inference.md) a [příkaz k odvození možnosti](../../../language-reference/statements/option-infer-statement.md).  
  
## <a name="characteristics-of-declared-variables"></a>Charakteristiky deklarovaných proměnných  
 *Doba života* proměnné je doba, po kterou je možné ji použít. Obecně platí, že proměnná existuje, pokud element, který ji deklaruje (například procedura nebo třída), nadále existují. Pokud proměnná nemusí pokračovat po dobu životnosti jejího obsahujícího prvku, nemusíte v deklaraci provádět žádné zvláštní akce. Pokud proměnná musí nadále existovat, než obsahuje element, můžete `Static` `Shared` do jejího příkazu zahrnout klíčové slovo or `Dim` . Další informace najdete v tématu [Doba života v Visual Basic](../declared-elements/lifetime.md).  
  
 *Rozsah* proměnné je sada veškerého kódu, který se na něj může odkazovat bez kvalifikovaného názvu. Rozsah proměnné je určen podle toho, kde je deklarována. Kód umístěný v dané oblasti může používat proměnné definované v této oblasti, aniž by bylo nutné kvalifikovat jejich názvy. Další informace najdete v tématu věnovaném [oboru v Visual Basic](../declared-elements/scope.md).  
  
 *Úroveň přístupu* proměnné je rozsah kódu, který má oprávnění k přístupu. To je určeno modifikátorem přístupu (například [veřejným](../../../language-reference/modifiers/public.md) nebo [soukromým](../../../language-reference/modifiers/private.md)), který použijete v `Dim` příkazu. Další informace najdete v tématu [úrovně přístupu v Visual Basic](../declared-elements/access-levels.md).  
  
## <a name="see-also"></a>Viz také

- [Postupy: Vytvoření nové proměnné](how-to-create-a-new-variable.md)
- [Postupy: Přesun dat do proměnné a z proměnné](how-to-move-data-into-and-out-of-a-variable.md)
- [Datové typy](../../../language-reference/data-types/index.md)
- [Proti](../../../language-reference/modifiers/protected.md)
- [Friend](../../../language-reference/modifiers/friend.md)
- [Tras](../../../language-reference/modifiers/static.md)
- [Deklarované charakteristiky elementů](../declared-elements/declared-element-characteristics.md)
- [Odvození místního typu](local-type-inference.md)
- [Option Infer – příkaz](../../../language-reference/statements/option-infer-statement.md)
