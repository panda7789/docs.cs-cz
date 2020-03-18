---
title: 'Postup: Přidání nebo odebrání položek seznamu řízení přístupu (pouze rozhraní .NET Framework)'
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708125"
---
# <a name="how-to-add-or-remove-access-control-list-entries-net-framework-only"></a>Postup: Přidání nebo odebrání položek seznamu řízení přístupu (pouze rozhraní .NET Framework)
Chcete-li přidat nebo odebrat položky seznamu řízení přístupu (ACL) do nebo ze souboru nebo adresáře, získejte ze souboru nebo adresáře <xref:System.Security.AccessControl.FileSecurity> objekt nebo <xref:System.Security.AccessControl.DirectorySecurity> z něj. Upravte objekt a potom jej aplikujte zpět na soubor nebo adresář.  
  
## <a name="add-or-remove-an-acl-entry-from-a-file"></a>Přidání nebo odebrání položky acl ze souboru  
  
1. Volání <xref:System.IO.File.GetAccessControl%2A?displayProperty=nameWithType> metody získat <xref:System.Security.AccessControl.FileSecurity> objekt, který obsahuje aktuální položky ACL souboru.  
  
2. Přidejte nebo odeberte <xref:System.Security.AccessControl.FileSecurity> položky ACL z objektu vráceného z kroku 1.  
  
3. Chcete-li použít změny, předajte <xref:System.Security.AccessControl.FileSecurity> objekt metodě. <xref:System.IO.File.SetAccessControl%2A?displayProperty=nameWithType>  
  
## <a name="add-or-remove-an-acl-entry-from-a-directory"></a>Přidání nebo odebrání položky seznamu ACL z adresáře  
  
1. Volání <xref:System.IO.Directory.GetAccessControl%2A?displayProperty=nameWithType> metody získat <xref:System.Security.AccessControl.DirectorySecurity> objekt, který obsahuje aktuální položky seznamu Řízení acl adresáře.  
  
2. Přidejte nebo odeberte <xref:System.Security.AccessControl.DirectorySecurity> položky ACL z objektu vráceného z kroku 1.  
  
3. Chcete-li použít změny, předajte <xref:System.Security.AccessControl.DirectorySecurity> objekt metodě. <xref:System.IO.Directory.SetAccessControl%2A?displayProperty=nameWithType>  
  
## <a name="example"></a>Příklad  
 Ke spuštění tohoto příkladu je nutné použít platný uživatelský nebo skupinový účet. Příklad používá <xref:System.IO.File> objekt. Použijte stejný postup <xref:System.IO.FileInfo>pro <xref:System.IO.Directory>, <xref:System.IO.DirectoryInfo> a třídy.

 [!code-csharp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/CS/sample.cs#1)]
 [!code-vb[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/VB/sample.vb#1)]  
