---
title: 'Postupy: Odstranění systémového prostředku (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Using statement [Visual Basic], disposing of system resources
- Visual Basic code, control flow
- system resources, disposing of
- resources [Visual Basic], disposing of system
- system resources
- Using statement [Visual Basic], Using...End Using
- Using block
ms.assetid: 8be2b239-8090-419b-8e7e-bcaa75b0ecc8
ms.openlocfilehash: c780ee1a174ad044593960bc30a3ee2e1f929390
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583148"
---
# <a name="how-to-dispose-of-a-system-resource-visual-basic"></a>Postupy: Odstranění systémového prostředku (Visual Basic)
Můžete použít `Using` blok k zajištění toho, aby systém odstranil prostředek, když váš kód ukončuje blok. To je užitečné v případě, že používáte systémový prostředek, který spotřebovává velké množství paměti, nebo že jiné komponenty mají být také používány.  
  
### <a name="to-dispose-of-a-database-connection-when-your-code-is-finished-with-it"></a>Vyřazení databázového připojení, když je kód dokončen  
  
1. Ujistěte se, že jste zahrnuli příslušný [příkaz Imports (obor názvů a typ .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) pro připojení k databázi na začátku zdrojového souboru (v tomto případě <xref:System.Data.SqlClient>).  
  
2. Vytvořte `Using` blok s příkazy `Using` a `End Using`. Uvnitř bloku vložte kód, který se zabývá připojením k databázi.  
  
3. Deklarujte připojení a vytvořte jeho instanci jako součást příkazu `Using`.  
  
    ```vb  
    ' Insert the following line at the beginning of your source file.  
    Imports System.Data.SqlClient  
    Public Sub AccessSql(ByVal s As String)  
        Using sqc As New System.Data.SqlClient.SqlConnection(s)  
            MsgBox("Connected with string """ & sqc.ConnectionString & """")  
        End Using  
    End Sub  
    ```  
  
     Systém uvolní prostředek bez ohledu na to, jakým způsobem ukončujete blok, včetně případu neošetřené výjimky.  
  
     Všimněte si, že nemůžete získat přístup k `sqc` mimo blok `Using`, protože jeho rozsah je omezen na blok.  
  
     Stejnou techniku můžete použít pro systémový prostředek, jako je například popisovač souboru nebo Obálka COM. @No__t_0 blok použijete, pokud chcete mít jistotu, že je prostředek k dispozici pro jiné součásti po ukončení bloku `Using`.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Data.SqlClient.SqlConnection>
- [Tok řízení](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [Rozhodovací struktury](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [Struktury smyčky](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Ostatní řídicí struktury](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
- [Vnořené řídicí struktury](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Příkaz Using](../../../../visual-basic/language-reference/statements/using-statement.md)
