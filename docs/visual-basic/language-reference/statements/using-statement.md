---
title: Using – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.using
helpviewer_keywords:
- resource disposal
- Try...Catch...Finally statements, equivalent to Using statement
- resources [Visual Basic], disposing
- Using statement [Visual Basic]
ms.assetid: 665d1580-dd54-4e96-a9a9-6be2a68948f1
ms.openlocfilehash: 819af63acb6a1f038300bcb999dcfb904eb8a457
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592087"
---
# <a name="using-statement-visual-basic"></a>Using – příkaz (Visual Basic)

Deklaruje začátek bloku `Using` a volitelně získá systémové prostředky, které blok ovládá.

## <a name="syntax"></a>Syntaxe

```vb
Using { resourcelist | resourceexpression }
    [ statements ]
End Using
```

## <a name="parts"></a>Součásti

|Termín|Definice|  
|---|---|  
|`resourcelist`|Vyžaduje se, pokud neposkytnete `resourceexpression`. Seznam jednoho nebo více systémových prostředků, které tyto ovládací prvky blokování `Using` odděleny čárkami.|  
|`resourceexpression`|Vyžaduje se, pokud neposkytnete `resourcelist`. Referenční proměnná nebo výraz odkazující na systémový prostředek, který má být ovládán tímto @no__t blok-0.|  
|`statements`|Volitelný parametr. Blok příkazů, které spouští blok `Using`.|  
|`End Using`|Povinný parametr. Ukončí definici bloku `Using` a uvolní všechny prostředky, které ovládací prvek IT ovládá.|  

 Každý prostředek v části `resourcelist` má následující syntaxi a části:

 `resourcename As New resourcetype [ ( [ arglist ] ) ]`

 -nebo-

 `resourcename As resourcetype = resourceexpression`

## <a name="resourcelist-parts"></a>resourceList části

|Termín|Definice|  
|---|---|  
|`resourcename`|Povinný parametr. Referenční proměnná, která odkazuje na systémový prostředek, který blokují ovládací prvky `Using`.|  
|`New`|Vyžaduje se, pokud příkaz `Using` získá prostředek. Pokud jste už tento prostředek získali, použijte druhou alternativu syntaxe.|  
|`resourcetype`|Povinný parametr. Třída prostředku Třída musí implementovat rozhraní <xref:System.IDisposable>.|  
|`arglist`|Volitelný parametr. Seznam argumentů, které předáváte konstruktoru za účelem vytvoření instance `resourcetype`. Viz [seznam parametrů](parameter-list.md).|  
|`resourceexpression`|Povinný parametr. Proměnná nebo výraz odkazující na systémový prostředek splňující požadavky `resourcetype`. Použijete-li druhou alternativu syntaxe, je nutné získat prostředek před předáním řízení příkazu `Using`.|  
  
## <a name="remarks"></a>Poznámky

 Někdy váš kód vyžaduje nespravovaný prostředek, jako je popisovač souboru, Obálka COM nebo připojení SQL. Blok `Using` zaručuje odstranění jednoho nebo více takových prostředků, když je kód dokončen. Díky tomu jsou k dispozici pro další kód pro použití.

 Spravované prostředky jsou odstraněny nástrojem .NET Framework uvolňování paměti (GC) bez dalšího kódování na vaší straně. Pro spravované prostředky nepotřebujete blok `Using`. K vynucení vyřazení spravovaného prostředku místo toho, aby se čekalo na uvolňování paměti, však stále můžete použít blok `Using`.

 Blok `Using` má tři části: pořízení, využití a vyřazení.

- *Akvizice* znamená vytvoření proměnné a její inicializaci, aby odkazovala na systémový prostředek. Příkaz `Using` může získat jeden nebo více prostředků, nebo můžete získat přesně jeden prostředek před vstupem do bloku a zadat ho do příkazu `Using`. Pokud zadáte `resourceexpression`, musíte získat prostředek před předáním řízení příkazu `Using`.

- *Použití* znamená přístup k prostředkům a provádění akcí s nimi. Příkazy mezi `Using` a `End Using` reprezentují využití prostředků.

- *Vyřazení* znamená volání metody <xref:System.IDisposable.Dispose%2A> u objektu v `resourcename`. Tím umožníte, aby objekt čistě ukončil své prostředky. Příkaz `End Using` uvolní prostředky v rámci ovládacího prvku bloku `Using`.

## <a name="behavior"></a>Chování

 Blok `Using` se chová jako konstrukce `Try`... `Finally`, ve které blok `Try` prostředky používá a že je k Dispose blok `Finally`. Z tohoto důvodu blok `Using` garantuje odstranění prostředků bez ohledu na to, jak tento blok ukončujete. To platí i v případě neošetřené výjimky, s výjimkou <xref:System.StackOverflowException>.

 Rozsah všech proměnných prostředků získaných příkazem `Using` je omezen na blok `Using`.

 Pokud zadáte více než jeden systémový prostředek v příkazu `Using`, efekt je stejný, jako při vnoření `Using` bloků mezi sebou.

 Pokud je `resourcename` `Nothing`, není provedeno žádné volání <xref:System.IDisposable.Dispose%2A> a není vyvolána žádná výjimka.

## <a name="structured-exception-handling-within-a-using-block"></a>Strukturované zpracování výjimek v bloku using

 Pokud potřebujete zpracovat výjimku, která může nastat v rámci bloku `Using`, můžete do ní přidat kompletní `Try`... `Finally`. Pokud potřebujete zpracovat případ, kde se příkaz `Using` v získání prostředku nezdařil, můžete otestovat a zjistit, zda je `resourcename` `Nothing`.

## <a name="structured-exception-handling-instead-of-a-using-block"></a>Strukturované zpracování výjimek namísto bloku using

 Pokud potřebujete lepší kontrolu nad získáním prostředků nebo potřebujete další kód v bloku `Finally`, můžete přepsat `Using` blok jako konstrukci `Try`... `Finally`. Následující příklad ukazuje kostru `Try` a `Using` konstrukcí, které jsou ekvivalentní získání a odstranění `resource`.

```vb
Using resource As New resourceType
    ' Insert code to work with resource.
End Using

' For the acquisition and disposal of resource, the following  
' Try construction is equivalent to the Using block.
Dim resource As New resourceType
Try
    ' Insert code to work with resource.
Finally
    If resource IsNot Nothing Then
        resource.Dispose()
    End If
End Try
```

> [!NOTE]
> Kód uvnitř bloku `Using` by neměl přiřazovat objekt v `resourcename` do jiné proměnné. Při ukončení bloku `Using` je prostředek vyřazený a druhá proměnná nemá přístup k prostředku, ke kterému odkazuje.

## <a name="example"></a>Příklad

 Následující příklad vytvoří soubor s názvem log. txt a zapíše dva řádky textu do souboru. Příklad také přečte stejný soubor a zobrazí řádky textu:

 Vzhledem k tomu, že třídy <xref:System.IO.TextWriter> a <xref:System.IO.TextReader> implementují rozhraní <xref:System.IDisposable>, může kód použít příkazy `Using` k zajištění toho, aby byl soubor správně uzavřen po operacích zápisu a čtení.

 [!code-vb[VbVbalrStatements#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#50)]

## <a name="see-also"></a>Viz také:

- <xref:System.IDisposable>
- [Příkaz Try...Catch...Finally](try-catch-finally-statement.md)
- [Postupy: Odstranění systémového prostředku @ no__t-0
