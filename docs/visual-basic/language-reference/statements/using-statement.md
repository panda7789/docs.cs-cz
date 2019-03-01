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
ms.openlocfilehash: 1cf0772bf4e9a77474849c59454617261475fa76
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56966083"
---
# <a name="using-statement-visual-basic"></a>Using – příkaz (Visual Basic)
Deklaruje začátku `Using` blokovat a volitelně získá systémové prostředky, které řídí bloku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Using { resourcelist | resourceexpression }  
    [ statements ]  
End Using  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`resourcelist`|Povinné, pokud nezadáte `resourceexpression`. Seznam jedné nebo více systémových prostředků, který tato `Using` blokovat ovládací prvky, oddělené čárkami.|  
|`resourceexpression`|Povinné, pokud nezadáte `resourcelist`. Odkaz na proměnnou nebo výraz odkazuje na systémový prostředek pro řízení situace `Using` bloku.|  
|`statements`|Volitelné. Blok příkazů, který `Using` blok.|  
|`End Using`|Povinný parametr. Ukončí definici `Using` bloku a spravované všechny prostředky, které ji řídí.|  
  
 Každý prostředek v `resourcelist` část má následující syntaxi a části:  
  
 `resourcename As New resourcetype [ ( [ arglist ] ) ]`  
  
 -nebo-  
  
 `resourcename As resourcetype = resourceexpression`  
  
## <a name="resourcelist-parts"></a>resourcelist částí  
  
|Termín|Definice|  
|---|---|  
|`resourcename`|Povinný parametr. Odkaz na proměnnou, která odkazuje na systémový prostředek, který `Using` blokovat ovládací prvky.|  
|`New`|Požadováno pokud `Using` příkaz získá prostředek. Pokud jste už zakoupili prostředku, použijte druhý alternativní syntaxi.|  
|`resourcetype`|Povinný parametr. Třída prostředku. Třída musí implementovat <xref:System.IDisposable> rozhraní.|  
|`arglist`|Volitelné. Seznam argumentů, které předáváte konstruktor pro vytvoření instance `resourcetype`. Zobrazit [seznam parametrů](../../../visual-basic/language-reference/statements/parameter-list.md).|  
|`resourceexpression`|Povinný parametr. Proměnné nebo výraz odkazuje na systémový prostředek splňující požadavky `resourcetype`. Pokud použijete druhý alternativní syntaxi, musíte získat zdroje před předáním řízení `Using` příkazu.|  
  
## <a name="remarks"></a>Poznámky  
 Váš kód vyžaduje někdy nespravovaný prostředek, jako je například popisovač souboru, obálky COM nebo připojení SQL. A `Using` bloku zaručuje k dispozici jeden nebo více těchto prostředků po dokončení se váš kód s nimi. Adaptéry tak budou k dispozici pro další kód používat.  
  
 Spravované prostředky jsou odstraněny ze systému uvolňování paměti rozhraní .NET Framework (GC) bez dalších kódování z vaší strany. Není nutné `Using` blok pro spravované prostředky. Ale můžete pořád použít `Using` bloku k vynucení uvolnění spravovaného prostředku, místo abyste čekali, systému uvolňování paměti.  
  
 A `Using` blok má tři části: získání, využití a vyřazení.  
  
-   *Získání* znamená, že vytváření proměnných a inicializuje ji k odkazování na systémový prostředek. `Using` Příkazu můžete získat jednu nebo více prostředků, nebo můžete získat přesně jeden prostředek před vstupem bloku a bude `Using` příkazu. Pokud zadáte `resourceexpression`, musíte získat zdroje před předáním řízení `Using` příkazu.  
  
-   *Využití* znamená, že přístup k prostředkům a provádění akcí s nimi. Příkazy mezi `Using` a `End Using` představují využití prostředků.  
  
-   *Vyřazení* znamená, že volání <xref:System.IDisposable.Dispose%2A> metodu na objekt v `resourcename`. To umožňuje objektu čistě ukončit jeho prostředky. `End Using` Příkaz uvolní prostředky v rámci `Using` bloku ovládacího prvku.  
  
## <a name="behavior"></a>Chování  
 A `Using` bloku se chová stejně jako `Try`... `Finally` konstrukce, ve kterém `Try` blok používá prostředky a `Finally` uvolní blok z nich. Z toho důvodu `Using` bloku zaručuje zacházení s prostředky, bez ohledu na to, jak ukončení bloku. To platí i v případě neošetřené výjimky, s výjimkou <xref:System.StackOverflowException>.  
  
 Obor proměnné každý prostředek získala `Using` příkaz je omezená na `Using` bloku.  
  
 Pokud zadáte více než jeden systémový prostředek v `Using` příkaz efekt je stejný, jako kdyby jste vnořené `Using` blokuje jednoho do jiného.  
  
 Pokud `resourcename` je `Nothing`, bez volání <xref:System.IDisposable.Dispose%2A> se provádí, a není vyvolána žádná výjimka.  
  
## <a name="structured-exception-handling-within-a-using-block"></a>Strukturované zpracování výjimek v rámci bloku pomocí  
 Pokud potřebujete ke zpracování výjimky, ke kterému může dojít v rámci `Using` blok, můžete přidat kompletní `Try`... `Finally` konstrukce k němu. Pokud budete potřebovat pro zpracování případu, kdy `Using` příkaz se nepovedlo úspěšně dokončit při získávání prostředku, můžete otestovat a zjistěte, jestli `resourcename` je `Nothing`.  
  
## <a name="structured-exception-handling-instead-of-a-using-block"></a>Namísto použití bloku zpracování strukturovaných výjimek  
 Pokud potřebujete lepší kontrolu nad pořízení prostředků, nebo potřebujete další kód v `Finally` blok, je možné přepsat `Using` blokovat, jako `Try`... `Finally` konstrukce. Následující příklad ukazuje osnovu `Try` a `Using` konstrukce, které jsou ekvivalentní v získávání a odstraňování `resource`.  
  
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
>  Kód uvnitř `Using` bloku by neměl přiřazení objektu v `resourcename` do jiné proměnné. Po ukončení `Using` bloku, prostředek je uvolněn a jiné proměnné nemůže přistupovat k prostředku, na kterou odkazuje.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří soubor, který má název log.txt a zapíše dva řádky textu do souboru. V příkladu také přečte Tento stejný soubor a zobrazí řádky textu.  
  
 Protože <xref:System.IO.TextWriter> a <xref:System.IO.TextReader> implementace třídy <xref:System.IDisposable> rozhraní, můžete použít kód `Using` příkazy k zajištění, že soubor je správně uzavřen po zápisu a operace čtení.  
  
 [!code-vb[VbVbalrStatements#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#50)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.IDisposable>
- [Příkaz Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Postupy: Odstranění systémového prostředku](../../../visual-basic/programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md)
