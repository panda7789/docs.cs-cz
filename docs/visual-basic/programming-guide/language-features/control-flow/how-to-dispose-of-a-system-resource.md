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
ms.openlocfilehash: cbb66934833da2bd6f0b797944dbb9c4df267cfc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-dispose-of-a-system-resource-visual-basic"></a>Postupy: Odstranění systémového prostředku (Visual Basic)
Můžete použít `Using` bloku zaručit, že systém uvolní prostředku při ukončení bloku kódu. To je užitečné, pokud používáte systémový prostředek, který využívá velké množství paměti, nebo že ostatní součásti také chcete použít.  
  
### <a name="to-dispose-of-a-database-connection-when-your-code-is-finished-with-it"></a>K uvolnění připojení databáze. Po dokončení se s ním kódu  
  
1.  Zajistěte, aby zahrnete odpovídající [příkaz Imports (Namespace .NET a typ)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) pro připojení k databázi na začátku zdrojového souboru (v tomto případě <xref:System.Data.SqlClient>).  
  
2.  Vytvoření `Using` blokovat s `Using` a `End Using` příkazy. Uvnitř bloku uveďte kód, který přistupuje k připojení k databázi.  
  
3.  Deklarování připojení a vytvořit její instanci v rámci `Using` příkaz.  
  
    ```  
    ' Insert the following line at the beginning of your source file.  
    Imports System.Data.SqlClient  
    Public Sub AccessSql(ByVal s As String)  
        Using sqc As New System.Data.SqlClient.SqlConnection(s)  
            MsgBox("Connected with string """ & sqc.ConnectionString & """")  
        End Using  
    End Sub  
    ```  
  
     Systém uvolní prostředku bez ohledu na to, jak byl ukončen blok, i v případě neošetřené výjimce.  
  
     Všimněte si, že nemáte přístup k `sqc` z mimo `Using` blokovat, protože její rozsah je omezený na bloku.  
  
     Tento stejný postup můžete použít na systémový prostředek, jako je například popisovač souboru nebo obálky COM. Můžete použít `Using` blokovat, pokud chcete mít jistotu opustit prostředek k dispozici pro jiné komponenty po zavření `Using` bloku.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Data.SqlClient.SqlConnection>  
 [Tok řízení](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [Rozhodovací struktury](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [Struktury smyčky](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [Ostatní řídicí struktury](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)  
 [Vnořené řídicí struktury](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [Příkaz Using](../../../../visual-basic/language-reference/statements/using-statement.md)
