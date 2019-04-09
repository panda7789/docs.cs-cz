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
# <a name="how-to-add-or-remove-access-control-list-entries-net-framework-only"></a><span data-ttu-id="9ebbe-102">Postupy: Přidávání a odebírání položek seznamu řízení přístupu (pouze rozhraní .NET Framework)</span><span class="sxs-lookup"><span data-stu-id="9ebbe-102">How to: Add or remove Access Control List entries (.NET Framework only)</span></span>
<span data-ttu-id="9ebbe-103">K přidávání a odebírání položek seznamu řízení přístupu (ACL) do nebo ze souboru nebo adresáře, získat <xref:System.Security.AccessControl.FileSecurity> nebo <xref:System.Security.AccessControl.DirectorySecurity> objektu souboru nebo adresáře.</span><span class="sxs-lookup"><span data-stu-id="9ebbe-103">To add or remove Access Control List (ACL) entries to or from a file or directory, get the <xref:System.Security.AccessControl.FileSecurity> or <xref:System.Security.AccessControl.DirectorySecurity> object from the file or directory.</span></span> <span data-ttu-id="9ebbe-104">Úpravy objektu a použijte ji zpět do souboru nebo adresáře.</span><span class="sxs-lookup"><span data-stu-id="9ebbe-104">Modify the object, and then apply it back to the file or directory.</span></span>  
  
## <a name="add-or-remove-an-acl-entry-from-a-file"></a><span data-ttu-id="9ebbe-105">Přidat nebo odebrat položku seznamu ACL souboru</span><span class="sxs-lookup"><span data-stu-id="9ebbe-105">Add or remove an ACL entry from a file</span></span>  
  
1.  <span data-ttu-id="9ebbe-106">Volání <xref:System.IO.File.GetAccessControl%2A?displayProperty=nameWithType> metodu k získání <xref:System.Security.AccessControl.FileSecurity> objekt, který obsahuje aktuální položky seznamu ACL souboru.</span><span class="sxs-lookup"><span data-stu-id="9ebbe-106">Call the <xref:System.IO.File.GetAccessControl%2A?displayProperty=nameWithType> method to get a <xref:System.Security.AccessControl.FileSecurity> object that contains the current ACL entries of a file.</span></span>  
  
2.  <span data-ttu-id="9ebbe-107">Přidávání a odebírání položek seznamu ACL z <xref:System.Security.AccessControl.FileSecurity> vrácen objekt z kroku 1.</span><span class="sxs-lookup"><span data-stu-id="9ebbe-107">Add or remove ACL entries from the <xref:System.Security.AccessControl.FileSecurity> object returned from step 1.</span></span>  
  
3. <span data-ttu-id="9ebbe-108">Aby se změny projevily, předejte <xref:System.Security.AccessControl.FileSecurity> do objektu <xref:System.IO.File.SetAccessControl%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="9ebbe-108">To apply the changes, pass the <xref:System.Security.AccessControl.FileSecurity> object to the <xref:System.IO.File.SetAccessControl%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="add-or-remove-an-acl-entry-from-a-directory"></a><span data-ttu-id="9ebbe-109">Přidat nebo odebrat položku seznamu ACL z adresáře</span><span class="sxs-lookup"><span data-stu-id="9ebbe-109">Add or remove an ACL entry from a directory</span></span>  
  
1.  <span data-ttu-id="9ebbe-110">Volání <xref:System.IO.Directory.GetAccessControl%2A?displayProperty=nameWithType> metodu k získání <xref:System.Security.AccessControl.DirectorySecurity> objekt, který obsahuje aktuální položky seznamu ACL adresáře.</span><span class="sxs-lookup"><span data-stu-id="9ebbe-110">Call the <xref:System.IO.Directory.GetAccessControl%2A?displayProperty=nameWithType> method to get a <xref:System.Security.AccessControl.DirectorySecurity> object that contains the current ACL entries of a directory.</span></span>  
  
2.  <span data-ttu-id="9ebbe-111">Přidávání a odebírání položek seznamu ACL z <xref:System.Security.AccessControl.DirectorySecurity> vrácen objekt z kroku 1.</span><span class="sxs-lookup"><span data-stu-id="9ebbe-111">Add or remove ACL entries from the <xref:System.Security.AccessControl.DirectorySecurity> object returned from step 1.</span></span>  
  
3.  <span data-ttu-id="9ebbe-112">Aby se změny projevily, předejte <xref:System.Security.AccessControl.DirectorySecurity> do objektu <xref:System.IO.Directory.SetAccessControl%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="9ebbe-112">To apply the changes, pass the <xref:System.Security.AccessControl.DirectorySecurity> object to the <xref:System.IO.Directory.SetAccessControl%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ebbe-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="9ebbe-113">Example</span></span>  
 <span data-ttu-id="9ebbe-114">Chcete-li spustit tento příklad, musíte použít platný uživatelský nebo skupinový účet.</span><span class="sxs-lookup"><span data-stu-id="9ebbe-114">You must use a valid user or group account to run this example.</span></span> <span data-ttu-id="9ebbe-115">V příkladu se používá <xref:System.IO.File> objektu.</span><span class="sxs-lookup"><span data-stu-id="9ebbe-115">The example uses a <xref:System.IO.File> object.</span></span> <span data-ttu-id="9ebbe-116">Použijte stejný postup <xref:System.IO.FileInfo>, <xref:System.IO.Directory>, a <xref:System.IO.DirectoryInfo> třídy.</span><span class="sxs-lookup"><span data-stu-id="9ebbe-116">Use the same procedure for the <xref:System.IO.FileInfo>, <xref:System.IO.Directory>, and <xref:System.IO.DirectoryInfo> classes.</span></span>

 [!code-csharp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/CS/sample.cs#1)]
 [!code-vb[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/VB/sample.vb#1)]  
