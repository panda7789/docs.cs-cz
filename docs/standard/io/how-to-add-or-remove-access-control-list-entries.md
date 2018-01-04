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
# <a name="how-to-add-or-remove-access-control-list-entries"></a><span data-ttu-id="32285-102">Postupy: Přidávání a odebírání položek seznamu řízení přístupu</span><span class="sxs-lookup"><span data-stu-id="32285-102">How to: Add or Remove Access Control List Entries</span></span>
<span data-ttu-id="32285-103">Přidat nebo odebrat položky seznamu řízení přístupu (ACL) do nebo ze souboru, <xref:System.Security.AccessControl.FileSecurity> nebo <xref:System.Security.AccessControl.DirectorySecurity> objekt musí být získaný soubor nebo adresář, upravit a potom se použijí zpět na soubor nebo adresář.</span><span class="sxs-lookup"><span data-stu-id="32285-103">To add or remove Access Control List (ACL) entries to or from a file, the <xref:System.Security.AccessControl.FileSecurity> or <xref:System.Security.AccessControl.DirectorySecurity> object must be obtained from the file or directory, modified, and then applied back to the file or directory.</span></span>  
  
### <a name="to-add-or-remove-an-acl-entry-from-a-file"></a><span data-ttu-id="32285-104">Přidat nebo odebrat položku seznamu ACL souboru</span><span class="sxs-lookup"><span data-stu-id="32285-104">To add or remove an ACL entry from a File</span></span>  
  
1.  <span data-ttu-id="32285-105">Volání <xref:System.IO.File.GetAccessControl%2A> metodu za účelem získání <xref:System.Security.AccessControl.FileSecurity> objekt, který obsahuje aktuální položky seznamů ACL souboru.</span><span class="sxs-lookup"><span data-stu-id="32285-105">Call the <xref:System.IO.File.GetAccessControl%2A> method to get a <xref:System.Security.AccessControl.FileSecurity> object that contains the current ACL entries of a file.</span></span>  
  
2.  <span data-ttu-id="32285-106">Přidat nebo odebrat položky seznamů ACL z <xref:System.Security.AccessControl.FileSecurity> objekt vrácená z kroku 1.</span><span class="sxs-lookup"><span data-stu-id="32285-106">Add or remove ACL entries from the <xref:System.Security.AccessControl.FileSecurity> object returned from step 1.</span></span>  
  
3.  <span data-ttu-id="32285-107">Předat <xref:System.Security.AccessControl.FileSecurity> do objektu <xref:System.IO.File.SetAccessControl%2A> metoda, aby se změny projevily.</span><span class="sxs-lookup"><span data-stu-id="32285-107">Pass the <xref:System.Security.AccessControl.FileSecurity> object to the <xref:System.IO.File.SetAccessControl%2A> method to apply the changes.</span></span>  
  
### <a name="to-add-or-remove-an-acl-entry-from-a-directory"></a><span data-ttu-id="32285-108">Přidat nebo odebrat z adresáře, položce seznamu ACL</span><span class="sxs-lookup"><span data-stu-id="32285-108">To add or remove an ACL entry from a Directory</span></span>  
  
1.  <span data-ttu-id="32285-109">Volání <xref:System.IO.Directory.GetAccessControl%2A> metodu za účelem získání <xref:System.Security.AccessControl.DirectorySecurity> objekt, který obsahuje aktuální položky seznamů ACL adresáře.</span><span class="sxs-lookup"><span data-stu-id="32285-109">Call the <xref:System.IO.Directory.GetAccessControl%2A> method to get a <xref:System.Security.AccessControl.DirectorySecurity> object that contains the current ACL entries of a directory.</span></span>  
  
2.  <span data-ttu-id="32285-110">Přidat nebo odebrat položky seznamů ACL z <xref:System.Security.AccessControl.DirectorySecurity> objekt vrácená z kroku 1.</span><span class="sxs-lookup"><span data-stu-id="32285-110">Add or remove ACL entries from the <xref:System.Security.AccessControl.DirectorySecurity> object returned from step 1.</span></span>  
  
3.  <span data-ttu-id="32285-111">Předat <xref:System.Security.AccessControl.DirectorySecurity> do objektu <xref:System.IO.Directory.SetAccessControl%2A> metoda, aby se změny projevily.</span><span class="sxs-lookup"><span data-stu-id="32285-111">Pass the <xref:System.Security.AccessControl.DirectorySecurity> object to the <xref:System.IO.Directory.SetAccessControl%2A> method to apply the changes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="32285-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="32285-112">Example</span></span>  
 [!code-cpp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/cpp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/cpp/sample.cpp#1)]
 [!code-csharp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/CS/sample.cs#1)]
 [!code-vb[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/VB/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="32285-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="32285-113">Compiling the Code</span></span>  
 <span data-ttu-id="32285-114">Je nutné zadat platný uživatel nebo skupina účtu pro spuštění tohoto příkladu.</span><span class="sxs-lookup"><span data-stu-id="32285-114">You must supply a valid user or group account to run this example.</span></span> <span data-ttu-id="32285-115">Tento příklad používá <xref:System.IO.File> objektu; ale stejný postup se používá pro <xref:System.IO.FileInfo>, <xref:System.IO.Directory>, a <xref:System.IO.DirectoryInfo> třídy.</span><span class="sxs-lookup"><span data-stu-id="32285-115">This example uses a <xref:System.IO.File> object; however, the same procedure is used for the <xref:System.IO.FileInfo>, <xref:System.IO.Directory>, and <xref:System.IO.DirectoryInfo> classes.</span></span>
