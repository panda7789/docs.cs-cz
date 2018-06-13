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
ms.openlocfilehash: 725eeb42dc5462022ac1a021c537d701929398ba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604962"
---
# <a name="using-statement-visual-basic"></a>Using – příkaz (Visual Basic)
Deklaruje začátku `Using` blokovat a volitelně získá systémové prostředky, které se řídí bloku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Using { resourcelist | resourceexpression }  
    [ statements ]  
End Using  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`resourcelist`|Vyžaduje, pokud nezadáte `resourceexpression`. Seznam jedné nebo více systémových prostředků, které tento `Using` blokovat ovládací prvky, oddělených čárkami.|  
|`resourceexpression`|Vyžaduje, pokud nezadáte `resourcelist`. Odkaz na proměnnou nebo výraz odkazující na systémový prostředek kontrolován to `Using` bloku.|  
|`statements`|Volitelné. Blok příkazů, `Using` blokovat spuštění.|  
|`End Using`|Požadováno. Ukončí definice `Using` bloku a spravované všechny prostředky, které se jimi řídí.|  
  
 Všechny prostředky v `resourcelist` část má následující syntaxe a částí:  
  
 `resourcename As New resourcetype [ ( [ arglist ] ) ]`  
  
 -nebo-  
  
 `resourcename As resourcetype = resourceexpression`  
  
## <a name="resourcelist-parts"></a>resourcelist částí  
  
|Termín|Definice|  
|---|---|  
|`resourcename`|Požadováno. Odkaz na proměnnou, která odkazuje na systémový prostředek, `Using` blokovat ovládací prvky.|  
|`New`|Požadováno pokud `Using` příkaz získá prostředek. Pokud jste už získali prostředku, použijte druhý alternativní syntaxe.|  
|`resourcetype`|Požadováno. Třída prostředku. Musí implementovat třídu <xref:System.IDisposable> rozhraní.|  
|`arglist`|Volitelné. Seznam argumentů, které jste předali do konstruktor k vytvoření instance `resourcetype`. V tématu [seznam parametrů](../../../visual-basic/language-reference/statements/parameter-list.md).|  
|`resourceexpression`|Požadováno. Proměnná nebo výraz, která odkazuje na systémový prostředek, které splňují požadavky na `resourcetype`. Pokud použijete druhý alternativní syntaxe, musíte získat prostředek před předáním řízení k `Using` příkaz.|  
  
## <a name="remarks"></a>Poznámky  
 Někdy kódu vyžaduje nespravovaný prostředek, například popisovač souboru, obálky COM nebo připojení SQL. A `Using` bloku zaručuje k dispozici jeden nebo více těchto zdrojů až po dokončení kódu s nimi. Díky je k dispozici pro ostatní kódu pro použití.  
  
 Spravované prostředky modulem garbage collector v rozhraní .NET Framework (GC) se odstraní bez další kódování z vaší strany. Není nutné `Using` blok pro spravované prostředky. Ale když můžete nadále používat `Using` bloku přinutit k dispozici prostředek spravované místo abyste čekali, bude systém uvolňování.  
  
 A `Using` bloku má tři části: akvizice, použití a uvolnění.  
  
-   *Získávání* znamená vytvoření proměnné a inicializací odkazovat na systémový prostředek. `Using` Příkaz můžete získat jeden nebo více prostředků, nebo můžete získat přesně jeden prostředek před vstupem bloku a zadejte jej do `Using` příkaz. Pokud zadáte `resourceexpression`, musíte získat prostředek před předáním řízení k `Using` příkaz.  
  
-   *Využití* znamená přístupu k prostředkům a provádění akcí s nimi. Příkazy mezi `Using` a `End Using` představují využití prostředků.  
  
-   *Uvolnění* znamená volání <xref:System.IDisposable.Dispose%2A> metoda objektu ve `resourcename`. To umožňuje objekt řádně ukončit jeho prostředky. `End Using` Příkaz uvolní prostředky v rámci `Using` řízení bloku.  
  
## <a name="behavior"></a>Chování  
 A `Using` bloku se chová stejně jako `Try`... `Finally` konstrukce, ve kterém `Try` bloku používá prostředky a `Finally` bloku uvolní z nich. Z toho důvodu `Using` bloku zaručuje uvolnění prostředků, bez ohledu na to, jak byl ukončen blok. To platí i v případě neošetřené výjimky, s výjimkou <xref:System.StackOverflowException>.  
  
 Obor proměnné každých prostředků se získávají pomocí `Using` příkaz je omezený na `Using` bloku.  
  
 Pokud zadáte více než jeden systémový prostředek v `Using` příkaz účinek je stejný jako v případě, že jste vnořené `Using` blokuje jednu v rámci jiného.  
  
 Pokud `resourcename` je `Nothing`, bez volání <xref:System.IDisposable.Dispose%2A> přišla a nedojde k výjimce.  
  
## <a name="structured-exception-handling-within-a-using-block"></a>Strukturované zpracování výjimek v rámci bloku pomocí  
 Pokud potřebujete ke zpracování výjimky, které může dojít v rámci `Using` blok, můžete přidat úplná `Try`... `Finally` konstrukce k němu. Pokud potřebujete zpracování případu, kdy `Using` příkaz není úspěšné při získávání prostředek, můžete otestovat a zjistěte, zda `resourcename` je `Nothing`.  
  
## <a name="structured-exception-handling-instead-of-a-using-block"></a>Strukturované zpracování namísto použití bloku výjimek  
 Pokud potřebujete lepší kontrolu nad získávání prostředků, nebo budete potřebovat další kód v `Finally` bloku, je možné přepsat `Using` blokovat jako `Try`... `Finally` konstrukce. Následující příklad ukazuje kostru `Try` a `Using` konstrukce, která odpovídají v získávání a odstraňování `resource`.  
  
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
>  Kód uvnitř `Using` bloku nesmí přiřaďte objekt v `resourcename` jiné proměnné. Po ukončení `Using` bloku, prostředek je zveřejněn a další proměnná nemá přístup k prostředku, na kterou odkazuje.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří soubor s názvem log.txt a zapíše dva řádky textu do souboru. Tento příklad také přečte Tento stejný soubor a zobrazí řádky textu.  
  
 Protože <xref:System.IO.TextWriter> a <xref:System.IO.TextReader> implementace třídy <xref:System.IDisposable> rozhraní, můžete použít kód `Using` příkazy, čímž zkontrolujte, zda je soubor správně uzavřený po zápisu a operace čtení.  
  
 [!code-vb[VbVbalrStatements#50](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/using-statement_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IDisposable>  
 [Příkaz Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [Postupy: Odstranění systémového prostředku](../../../visual-basic/programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md)
