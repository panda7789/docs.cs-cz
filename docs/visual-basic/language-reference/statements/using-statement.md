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
ms.openlocfilehash: 346a26ad5751599831d8b0d3e0497e4d488eb76c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957536"
---
# <a name="using-statement-visual-basic"></a>Using – příkaz (Visual Basic)
Deklaruje začátek `Using` bloku a volitelně získá systémové prostředky, které blok ovládá.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Using { resourcelist | resourceexpression }  
    [ statements ]  
End Using  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`resourcelist`|Vyžaduje se `resourceexpression`, pokud nezadáte. Seznam jednoho nebo více systémových prostředků, které tento `Using` blok ovládá, oddělený čárkami.|  
|`resourceexpression`|Vyžaduje se `resourcelist`, pokud nezadáte. Referenční proměnná nebo výraz odkazující na systémový prostředek, který má být ovládán pomocí `Using` tohoto bloku.|  
|`statements`|Volitelný parametr. Blok příkazů, které `Using` blok spouští.|  
|`End Using`|Povinný parametr. Ukončí definici `Using` bloku a uvolní všechny prostředky, které ovládací prvek IT ovládá.|  
  
 Každý prostředek v `resourcelist` části má následující syntaxi a části:  
  
 `resourcename As New resourcetype [ ( [ arglist ] ) ]`  
  
 -nebo-  
  
 `resourcename As resourcetype = resourceexpression`  
  
## <a name="resourcelist-parts"></a>resourceList části  
  
|Termín|Definice|  
|---|---|  
|`resourcename`|Povinný parametr. Referenční proměnná, která odkazuje na systémový prostředek, který `Using` blok ovládá.|  
|`New`|Vyžaduje se, `Using` Pokud příkaz získá prostředek. Pokud jste už tento prostředek získali, použijte druhou alternativu syntaxe.|  
|`resourcetype`|Povinný parametr. Třída prostředku Třída musí implementovat <xref:System.IDisposable> rozhraní.|  
|`arglist`|Volitelný parametr. Seznam argumentů, které předáte konstruktoru pro vytvoření instance `resourcetype`. Viz [seznam parametrů](../../../visual-basic/language-reference/statements/parameter-list.md).|  
|`resourceexpression`|Povinný parametr. Proměnná nebo výraz odkazující na prostředek systému splňující požadavky `resourcetype`. Použijete-li druhou alternativu syntaxe, je nutné získat prostředek před předáním řízení `Using` příkazu.|  
  
## <a name="remarks"></a>Poznámky  
 Někdy váš kód vyžaduje nespravovaný prostředek, jako je popisovač souboru, Obálka COM nebo připojení SQL. `Using` Blok garantuje vyřazení jednoho nebo více takových prostředků, když je kód dokončen. Díky tomu jsou k dispozici pro další kód pro použití.  
  
 Spravované prostředky jsou odstraněny nástrojem .NET Framework uvolňování paměti (GC) bez dalšího kódování na vaší straně. Nepotřebujete `Using` blok pro spravované prostředky. Nicméně můžete i nadále používat `Using` blok k vynucení odstranění spravovaného prostředku místo čekání na systém uvolňování paměti.  
  
 `Using` Blok má tři části: pořízení, využití a vyřazení.  
  
- *Akvizice* znamená vytvoření proměnné a její inicializaci, aby odkazovala na systémový prostředek. Příkaz může získat jeden nebo více prostředků, nebo můžete získat přesně jeden prostředek před vstupem do bloku a dodat ho `Using` do příkazu. `Using` Pokud zadáte `resourceexpression`, je nutné získat prostředek před předáním řízení `Using` příkazu.  
  
- *Použití* znamená přístup k prostředkům a provádění akcí s nimi. Příkazy `Using` a`End Using` reprezentují využití prostředků.  
  
- *Vyřazení* znamená volání <xref:System.IDisposable.Dispose%2A> metody u objektu v `resourcename`. Tím umožníte, aby objekt čistě ukončil své prostředky. Příkaz uvolní prostředky `Using` v rámci ovládacího prvku bloku. `End Using`  
  
## <a name="behavior"></a>Chování  
 Blok `Using` se chová `Try`jako... konstrukce, ve `Try` které blok používá prostředky a který `Finally` blokuje jejich uvolnění. `Finally` Proto `Using` blok garantuje vyřazení prostředků bez ohledu na to, jak tento blok ukončujete. To platí i v případě neošetřené výjimky, s výjimkou <xref:System.StackOverflowException>.  
  
 Rozsah všech proměnných prostředků získaných `Using` příkazem je omezen `Using` na blok.  
  
 Pokud zadáte více než jeden systémový prostředek v `Using` příkazu, efekt je stejný, jako by byl vnořený `Using` blok v rámci jiného.  
  
 Pokud `resourcename` <xref:System.IDisposable.Dispose%2A> je `Nothing`, žádné volání není provedeno a není vyvolána žádná výjimka.  
  
## <a name="structured-exception-handling-within-a-using-block"></a>Strukturované zpracování výjimek v bloku using  
 Pokud potřebujete zpracovat výjimku, ke které může dojít v rámci `Using` bloku, můžete přidat úplnou `Try`... `Finally` konstrukce. Pokud potřebujete zpracovat případ, kde `Using` se příkaz při získání prostředku nezdařil, můžete otestovat a zjistit, zda `resourcename` je `Nothing`.  
  
## <a name="structured-exception-handling-instead-of-a-using-block"></a>Strukturované zpracování výjimek namísto bloku using  
 Pokud potřebujete lepší kontrolu nad získáním prostředků nebo potřebujete další kód v `Finally` bloku, můžete tento `Using` blok přepsat jako `Try`... `Finally` konstrukce. Následující příklad ukazuje kostru `Try` a `Using` konstrukce, které jsou ekvivalentní při získávání a vyřazení `resource`.  
  
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
> Kód uvnitř `Using` bloku by neměl přiřazovat objekt v `resourcename` jiné proměnné. Při ukončení `Using` bloku je prostředek vyřazen a druhá proměnná nemá přístup k prostředku, ke kterému odkazuje.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří soubor s názvem log. txt a zapíše dva řádky textu do souboru. Příklad také přečte stejný soubor a zobrazí řádky textu.  
  
 Vzhledem k tomu <xref:System.IO.TextReader> , že třídy <xref:System.IDisposable> `Using` a implementují rozhraní, může kód použít příkazy, aby bylo zajištěno, že soubor je po operacích zápisu a čtení správně uzavřen. <xref:System.IO.TextWriter>  
  
 [!code-vb[VbVbalrStatements#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#50)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IDisposable>
- [Příkaz Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Postupy: Odstranění systémového prostředku](../../../visual-basic/programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md)
