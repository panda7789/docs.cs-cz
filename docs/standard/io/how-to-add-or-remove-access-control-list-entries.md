---
title: 'Postupy: Přidávání a odebírání položek seznamu řízení přístupu (pouze rozhraní .NET Framework)'
ms.date: 01/14/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ACEs [.NET Framework]
- ACLs [.NET Framework]
- access control entries [.NET Framework]
- I/O [.NET Framework], access control list entries
- access control lists [.NET Framework]
ms.assetid: 53758b39-bd9b-4640-bb04-cad5ed8d0abf
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 645c4ea76509bf488b62669f65e03d3690fd5a05
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59103828"
---
# <a name="how-to-add-or-remove-access-control-list-entries-net-framework-only"></a>Postupy: Přidávání a odebírání položek seznamu řízení přístupu (pouze rozhraní .NET Framework)
K přidávání a odebírání položek seznamu řízení přístupu (ACL) do nebo ze souboru nebo adresáře, získat <xref:System.Security.AccessControl.FileSecurity> nebo <xref:System.Security.AccessControl.DirectorySecurity> objektu souboru nebo adresáře. Úpravy objektu a použijte ji zpět do souboru nebo adresáře.  
  
## <a name="add-or-remove-an-acl-entry-from-a-file"></a>Přidat nebo odebrat položku seznamu ACL souboru  
  
1.  Volání <xref:System.IO.File.GetAccessControl%2A?displayProperty=nameWithType> metodu k získání <xref:System.Security.AccessControl.FileSecurity> objekt, který obsahuje aktuální položky seznamu ACL souboru.  
  
2.  Přidávání a odebírání položek seznamu ACL z <xref:System.Security.AccessControl.FileSecurity> vrácen objekt z kroku 1.  
  
3. Aby se změny projevily, předejte <xref:System.Security.AccessControl.FileSecurity> do objektu <xref:System.IO.File.SetAccessControl%2A?displayProperty=nameWithType> metoda.  
  
## <a name="add-or-remove-an-acl-entry-from-a-directory"></a>Přidat nebo odebrat položku seznamu ACL z adresáře  
  
1.  Volání <xref:System.IO.Directory.GetAccessControl%2A?displayProperty=nameWithType> metodu k získání <xref:System.Security.AccessControl.DirectorySecurity> objekt, který obsahuje aktuální položky seznamu ACL adresáře.  
  
2.  Přidávání a odebírání položek seznamu ACL z <xref:System.Security.AccessControl.DirectorySecurity> vrácen objekt z kroku 1.  
  
3.  Aby se změny projevily, předejte <xref:System.Security.AccessControl.DirectorySecurity> do objektu <xref:System.IO.Directory.SetAccessControl%2A?displayProperty=nameWithType> metoda.  
  
## <a name="example"></a>Příklad  
 Chcete-li spustit tento příklad, musíte použít platný uživatelský nebo skupinový účet. V příkladu se používá <xref:System.IO.File> objektu. Použijte stejný postup <xref:System.IO.FileInfo>, <xref:System.IO.Directory>, a <xref:System.IO.DirectoryInfo> třídy.

 [!code-csharp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/CS/sample.cs#1)]
 [!code-vb[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/VB/sample.vb#1)]  
