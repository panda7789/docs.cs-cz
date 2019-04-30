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
ms.openlocfilehash: e3594db036edc3a6288b0373737c1ee26a691a57
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61906734"
---
# <a name="how-to-dispose-of-a-system-resource-visual-basic"></a>Postupy: Odstranění systémového prostředku (Visual Basic)
Můžete použít `Using` bloku zaručí, že systém odstraňuje prostředku při opuštění bloku kódu. To je užitečné, pokud používáte systémového prostředku, která spotřebovává velké množství paměti, nebo jiné komponenty také chcete použít.  
  
### <a name="to-dispose-of-a-database-connection-when-your-code-is-finished-with-it"></a>K uvolnění připojení databáze. Po dokončení se s ním kódu  
  
1. Nezapomeňte zadat odpovídající [příkaz Imports (Namespace .NET a typ)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) pro připojení k databázi na začátku zdrojového souboru (v tomto případě <xref:System.Data.SqlClient>).  
  
2. Vytvoření `Using` blokovat s `Using` a `End Using` příkazy. Uvnitř bloku vložte kód, který se zabývá připojení k databázi.  
  
3. Deklarace připojení a vytvořte její instanci v rámci `Using` příkazu.  
  
    ```  
    ' Insert the following line at the beginning of your source file.  
    Imports System.Data.SqlClient  
    Public Sub AccessSql(ByVal s As String)  
        Using sqc As New System.Data.SqlClient.SqlConnection(s)  
            MsgBox("Connected with string """ & sqc.ConnectionString & """")  
        End Using  
    End Sub  
    ```  
  
     Systém odstraňuje prostředků bez ohledu na to, jak ukončení bloku i v případě neošetřené výjimce.  
  
     Všimněte si, že nemáte přístup `sqc` z mimo `Using` blokovat, protože jeho rozsah je omezen na blok.  
  
     Tento stejný postup můžete použít na systémový prostředek, jako je například popisovač souboru nebo obálky COM. Můžete použít `Using` blokovat, pokud chcete mít jistotu ponechat prostředek k dispozici pro jiné komponenty po zavření `Using` bloku.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Data.SqlClient.SqlConnection>
- [Tok řízení](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [Rozhodovací struktury](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [Struktury smyčky](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Ostatní řídicí struktury](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
- [Vnořené řídicí struktury](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Příkaz Using](../../../../visual-basic/language-reference/statements/using-statement.md)
