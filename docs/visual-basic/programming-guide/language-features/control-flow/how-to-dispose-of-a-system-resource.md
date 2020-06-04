---
title: 'Postupy: Odstranění systémového prostředku'
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
ms.openlocfilehash: dd15c6746628f45b072d46eea40051ed9afb7921
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403495"
---
# <a name="how-to-dispose-of-a-system-resource-visual-basic"></a>Postupy: Odstranění systémového prostředku (Visual Basic)
Blok můžete použít `Using` k zajištění, že systém uvolní prostředek, když váš kód ukončuje blok. To je užitečné v případě, že používáte systémový prostředek, který spotřebovává velké množství paměti, nebo že jiné komponenty mají být také používány.  
  
### <a name="to-dispose-of-a-database-connection-when-your-code-is-finished-with-it"></a>Vyřazení databázového připojení, když je kód dokončen  
  
1. Ujistěte se, že jste zahrnuli příslušný [příkaz Imports (obor názvů a typ .NET)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md) pro připojení k databázi na začátku zdrojového souboru (v tomto případě <xref:System.Data.SqlClient> ).  
  
2. Vytvořte `Using` blok s `Using` `End Using` příkazy a. Uvnitř bloku vložte kód, který se zabývá připojením k databázi.  
  
3. Deklarujte připojení a vytvořte jeho instanci jako součást `Using` příkazu.  
  
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
  
     Všimněte si, že nemůžete získat přístup `sqc` z vnějšího `Using` bloku, protože jeho rozsah je omezen na blok.  
  
     Stejnou techniku můžete použít pro systémový prostředek, jako je například popisovač souboru nebo Obálka COM. Blok můžete použít, `Using` Pokud chcete mít jistotu, že je prostředek k dispozici pro jiné součásti po ukončení `Using` bloku.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Data.SqlClient.SqlConnection>
- [Tok řízení](index.md)
- [Struktury rozhodování](decision-structures.md)
- [Struktury smyčky](loop-structures.md)
- [Ostatní řídicí struktury](other-control-structures.md)
- [Vnořené řídicí struktury](nested-control-structures.md)
- [Using – příkaz](../../../language-reference/statements/using-statement.md)
