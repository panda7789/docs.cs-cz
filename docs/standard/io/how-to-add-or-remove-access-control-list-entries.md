---
title: 'Postupy: přidávání a odebírání položek seznamu Access Control (pouze .NET Framework)'
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
ms.openlocfilehash: 5f41c518b8732adff95593cab29d7085adcc9ab3
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708125"
---
# <a name="how-to-add-or-remove-access-control-list-entries-net-framework-only"></a>Postupy: přidávání a odebírání položek seznamu Access Control (pouze .NET Framework)
Chcete-li přidat nebo odebrat položky seznamu Access Control (seznam ACL) do souboru nebo adresáře nebo z něj, získejte objekt <xref:System.Security.AccessControl.FileSecurity> nebo <xref:System.Security.AccessControl.DirectorySecurity> ze souboru nebo adresáře. Upravte objekt a pak ho použijte zpátky do souboru nebo adresáře.  
  
## <a name="add-or-remove-an-acl-entry-from-a-file"></a>Přidat nebo odebrat položku seznamu řízení přístupu (ACL) ze souboru  
  
1. Voláním metody <xref:System.IO.File.GetAccessControl%2A?displayProperty=nameWithType> získáte objekt <xref:System.Security.AccessControl.FileSecurity>, který obsahuje aktuální položky seznamu ACL souboru.  
  
2. Přidá nebo odebere položky seznamu řízení přístupu z objektu <xref:System.Security.AccessControl.FileSecurity> vráceného z kroku 1.  
  
3. Chcete-li použít změny, předejte objekt <xref:System.Security.AccessControl.FileSecurity> do metody <xref:System.IO.File.SetAccessControl%2A?displayProperty=nameWithType>.  
  
## <a name="add-or-remove-an-acl-entry-from-a-directory"></a>Přidat nebo odebrat položku seznamu řízení přístupu (ACL) z adresáře  
  
1. Voláním metody <xref:System.IO.Directory.GetAccessControl%2A?displayProperty=nameWithType> získáte objekt <xref:System.Security.AccessControl.DirectorySecurity>, který obsahuje aktuální položky seznamu ACL adresáře.  
  
2. Přidá nebo odebere položky seznamu řízení přístupu z objektu <xref:System.Security.AccessControl.DirectorySecurity> vráceného z kroku 1.  
  
3. Chcete-li použít změny, předejte objekt <xref:System.Security.AccessControl.DirectorySecurity> do metody <xref:System.IO.Directory.SetAccessControl%2A?displayProperty=nameWithType>.  
  
## <a name="example"></a>Příklad  
 Chcete-li spustit tento příklad, je nutné použít platný účet uživatele nebo skupiny. V příkladu se používá objekt <xref:System.IO.File>. Pro třídy <xref:System.IO.FileInfo>, <xref:System.IO.Directory>a <xref:System.IO.DirectoryInfo> použijte stejný postup.

 [!code-csharp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/CS/sample.cs#1)]
 [!code-vb[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/VB/sample.vb#1)]  
