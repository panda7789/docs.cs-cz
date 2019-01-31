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
ms.openlocfilehash: ea1059f541d2449a1a2d5dca1644ce8d9a553e40
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55283345"
---
# <a name="how-to-add-or-remove-access-control-list-entries-net-framework-only"></a><span data-ttu-id="9cb4f-102">Postupy: Přidávání a odebírání položek seznamu řízení přístupu (pouze rozhraní .NET Framework)</span><span class="sxs-lookup"><span data-stu-id="9cb4f-102">How to: Add or remove Access Control List entries (.NET Framework only)</span></span>
<span data-ttu-id="9cb4f-103">K přidávání a odebírání položek seznamu řízení přístupu (ACL) do nebo ze souboru nebo adresáře, získat <xref:System.Security.AccessControl.FileSecurity> nebo <xref:System.Security.AccessControl.DirectorySecurity> objektu souboru nebo adresáře.</span><span class="sxs-lookup"><span data-stu-id="9cb4f-103">To add or remove Access Control List (ACL) entries to or from a file or directory, get the <xref:System.Security.AccessControl.FileSecurity> or <xref:System.Security.AccessControl.DirectorySecurity> object from the file or directory.</span></span> <span data-ttu-id="9cb4f-104">Úpravy objektu a použijte ji zpět do souboru nebo adresáře.</span><span class="sxs-lookup"><span data-stu-id="9cb4f-104">Modify the object, and then apply it back to the file or directory.</span></span>  
  
## <a name="add-or-remove-an-acl-entry-from-a-file"></a><span data-ttu-id="9cb4f-105">Přidat nebo odebrat položku seznamu ACL souboru</span><span class="sxs-lookup"><span data-stu-id="9cb4f-105">Add or remove an ACL entry from a file</span></span>  
  
1.  <span data-ttu-id="9cb4f-106">Volání <xref:System.IO.File.GetAccessControl%2A?displayProperty=nameWithType> metodu k získání <xref:System.Security.AccessControl.FileSecurity> objekt, který obsahuje aktuální položky seznamu ACL souboru.</span><span class="sxs-lookup"><span data-stu-id="9cb4f-106">Call the <xref:System.IO.File.GetAccessControl%2A?displayProperty=nameWithType> method to get a <xref:System.Security.AccessControl.FileSecurity> object that contains the current ACL entries of a file.</span></span>  
  
2.  <span data-ttu-id="9cb4f-107">Přidávání a odebírání položek seznamu ACL z <xref:System.Security.AccessControl.FileSecurity> vrácen objekt z kroku 1.</span><span class="sxs-lookup"><span data-stu-id="9cb4f-107">Add or remove ACL entries from the <xref:System.Security.AccessControl.FileSecurity> object returned from step 1.</span></span>  
  
3. <span data-ttu-id="9cb4f-108">Aby se změny projevily, předejte <xref:System.Security.AccessControl.FileSecurity> do objektu <xref:System.IO.File.SetAccessControl%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="9cb4f-108">To apply the changes, pass the <xref:System.Security.AccessControl.FileSecurity> object to the <xref:System.IO.File.SetAccessControl%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="add-or-remove-an-acl-entry-from-a-directory"></a><span data-ttu-id="9cb4f-109">Přidat nebo odebrat položku seznamu ACL z adresáře</span><span class="sxs-lookup"><span data-stu-id="9cb4f-109">Add or remove an ACL entry from a directory</span></span>  
  
1.  <span data-ttu-id="9cb4f-110">Volání <xref:System.IO.Directory.GetAccessControl%2A?displayProperty=nameWithType> metodu k získání <xref:System.Security.AccessControl.DirectorySecurity> objekt, který obsahuje aktuální položky seznamu ACL adresáře.</span><span class="sxs-lookup"><span data-stu-id="9cb4f-110">Call the <xref:System.IO.Directory.GetAccessControl%2A?displayProperty=nameWithType> method to get a <xref:System.Security.AccessControl.DirectorySecurity> object that contains the current ACL entries of a directory.</span></span>  
  
2.  <span data-ttu-id="9cb4f-111">Přidávání a odebírání položek seznamu ACL z <xref:System.Security.AccessControl.DirectorySecurity> vrácen objekt z kroku 1.</span><span class="sxs-lookup"><span data-stu-id="9cb4f-111">Add or remove ACL entries from the <xref:System.Security.AccessControl.DirectorySecurity> object returned from step 1.</span></span>  
  
3.  <span data-ttu-id="9cb4f-112">Aby se změny projevily, předejte <xref:System.Security.AccessControl.DirectorySecurity> do objektu <xref:System.IO.Directory.SetAccessControl%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="9cb4f-112">To apply the changes, pass the <xref:System.Security.AccessControl.DirectorySecurity> object to the <xref:System.IO.Directory.SetAccessControl%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9cb4f-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="9cb4f-113">Example</span></span>  
 <span data-ttu-id="9cb4f-114">Chcete-li spustit tento příklad, musíte použít platný uživatelský nebo skupinový účet.</span><span class="sxs-lookup"><span data-stu-id="9cb4f-114">You must use a valid user or group account to run this example.</span></span> <span data-ttu-id="9cb4f-115">V příkladu se používá <xref:System.IO.File> objektu.</span><span class="sxs-lookup"><span data-stu-id="9cb4f-115">The example uses a <xref:System.IO.File> object.</span></span> <span data-ttu-id="9cb4f-116">Použijte stejný postup <xref:System.IO.FileInfo>, <xref:System.IO.Directory>, a <xref:System.IO.DirectoryInfo> třídy.</span><span class="sxs-lookup"><span data-stu-id="9cb4f-116">Use the same procedure for the <xref:System.IO.FileInfo>, <xref:System.IO.Directory>, and <xref:System.IO.DirectoryInfo> classes.</span></span>

 [!code-csharp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/CS/sample.cs#1)]
 [!code-vb[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/VB/sample.vb#1)]  
  
