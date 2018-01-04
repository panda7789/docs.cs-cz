---
title: "Postupy: Přidávání a odebírání položek seznamu řízení přístupu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 988fd354caa5fcc716107087242ead113c9a9939
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-add-or-remove-access-control-list-entries"></a>Postupy: Přidávání a odebírání položek seznamu řízení přístupu
Přidat nebo odebrat položky seznamu řízení přístupu (ACL) do nebo ze souboru, <xref:System.Security.AccessControl.FileSecurity> nebo <xref:System.Security.AccessControl.DirectorySecurity> objekt musí být získaný soubor nebo adresář, upravit a potom se použijí zpět na soubor nebo adresář.  
  
### <a name="to-add-or-remove-an-acl-entry-from-a-file"></a>Přidat nebo odebrat položku seznamu ACL souboru  
  
1.  Volání <xref:System.IO.File.GetAccessControl%2A> metodu za účelem získání <xref:System.Security.AccessControl.FileSecurity> objekt, který obsahuje aktuální položky seznamů ACL souboru.  
  
2.  Přidat nebo odebrat položky seznamů ACL z <xref:System.Security.AccessControl.FileSecurity> objekt vrácená z kroku 1.  
  
3.  Předat <xref:System.Security.AccessControl.FileSecurity> do objektu <xref:System.IO.File.SetAccessControl%2A> metoda, aby se změny projevily.  
  
### <a name="to-add-or-remove-an-acl-entry-from-a-directory"></a>Přidat nebo odebrat z adresáře, položce seznamu ACL  
  
1.  Volání <xref:System.IO.Directory.GetAccessControl%2A> metodu za účelem získání <xref:System.Security.AccessControl.DirectorySecurity> objekt, který obsahuje aktuální položky seznamů ACL adresáře.  
  
2.  Přidat nebo odebrat položky seznamů ACL z <xref:System.Security.AccessControl.DirectorySecurity> objekt vrácená z kroku 1.  
  
3.  Předat <xref:System.Security.AccessControl.DirectorySecurity> do objektu <xref:System.IO.Directory.SetAccessControl%2A> metoda, aby se změny projevily.  
  
## <a name="example"></a>Příklad  
 [!code-cpp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/cpp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/cpp/sample.cpp#1)]
 [!code-csharp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/CS/sample.cs#1)]
 [!code-vb[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/VB/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Je nutné zadat platný uživatel nebo skupina účtu pro spuštění tohoto příkladu. Tento příklad používá <xref:System.IO.File> objektu; ale stejný postup se používá pro <xref:System.IO.FileInfo>, <xref:System.IO.Directory>, a <xref:System.IO.DirectoryInfo> třídy.
