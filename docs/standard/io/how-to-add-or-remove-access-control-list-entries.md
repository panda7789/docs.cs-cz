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
# <a name="how-to-add-or-remove-access-control-list-entries-net-framework-only"></a><span data-ttu-id="e3f50-102">Postup: Přidání nebo odebrání položek seznamu řízení přístupu (pouze rozhraní .NET Framework)</span><span class="sxs-lookup"><span data-stu-id="e3f50-102">How to: Add or remove Access Control List entries (.NET Framework only)</span></span>
<span data-ttu-id="e3f50-103">Chcete-li přidat nebo odebrat položky seznamu řízení přístupu (ACL) do nebo ze souboru nebo adresáře, získejte ze souboru nebo adresáře <xref:System.Security.AccessControl.FileSecurity> objekt nebo <xref:System.Security.AccessControl.DirectorySecurity> z něj.</span><span class="sxs-lookup"><span data-stu-id="e3f50-103">To add or remove Access Control List (ACL) entries to or from a file or directory, get the <xref:System.Security.AccessControl.FileSecurity> or <xref:System.Security.AccessControl.DirectorySecurity> object from the file or directory.</span></span> <span data-ttu-id="e3f50-104">Upravte objekt a potom jej aplikujte zpět na soubor nebo adresář.</span><span class="sxs-lookup"><span data-stu-id="e3f50-104">Modify the object, and then apply it back to the file or directory.</span></span>  
  
## <a name="add-or-remove-an-acl-entry-from-a-file"></a><span data-ttu-id="e3f50-105">Přidání nebo odebrání položky acl ze souboru</span><span class="sxs-lookup"><span data-stu-id="e3f50-105">Add or remove an ACL entry from a file</span></span>  
  
1. <span data-ttu-id="e3f50-106">Volání <xref:System.IO.File.GetAccessControl%2A?displayProperty=nameWithType> metody získat <xref:System.Security.AccessControl.FileSecurity> objekt, který obsahuje aktuální položky ACL souboru.</span><span class="sxs-lookup"><span data-stu-id="e3f50-106">Call the <xref:System.IO.File.GetAccessControl%2A?displayProperty=nameWithType> method to get a <xref:System.Security.AccessControl.FileSecurity> object that contains the current ACL entries of a file.</span></span>  
  
2. <span data-ttu-id="e3f50-107">Přidejte nebo odeberte <xref:System.Security.AccessControl.FileSecurity> položky ACL z objektu vráceného z kroku 1.</span><span class="sxs-lookup"><span data-stu-id="e3f50-107">Add or remove ACL entries from the <xref:System.Security.AccessControl.FileSecurity> object returned from step 1.</span></span>  
  
3. <span data-ttu-id="e3f50-108">Chcete-li použít změny, předajte <xref:System.Security.AccessControl.FileSecurity> objekt metodě. <xref:System.IO.File.SetAccessControl%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="e3f50-108">To apply the changes, pass the <xref:System.Security.AccessControl.FileSecurity> object to the <xref:System.IO.File.SetAccessControl%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="add-or-remove-an-acl-entry-from-a-directory"></a><span data-ttu-id="e3f50-109">Přidání nebo odebrání položky seznamu ACL z adresáře</span><span class="sxs-lookup"><span data-stu-id="e3f50-109">Add or remove an ACL entry from a directory</span></span>  
  
1. <span data-ttu-id="e3f50-110">Volání <xref:System.IO.Directory.GetAccessControl%2A?displayProperty=nameWithType> metody získat <xref:System.Security.AccessControl.DirectorySecurity> objekt, který obsahuje aktuální položky seznamu Řízení acl adresáře.</span><span class="sxs-lookup"><span data-stu-id="e3f50-110">Call the <xref:System.IO.Directory.GetAccessControl%2A?displayProperty=nameWithType> method to get a <xref:System.Security.AccessControl.DirectorySecurity> object that contains the current ACL entries of a directory.</span></span>  
  
2. <span data-ttu-id="e3f50-111">Přidejte nebo odeberte <xref:System.Security.AccessControl.DirectorySecurity> položky ACL z objektu vráceného z kroku 1.</span><span class="sxs-lookup"><span data-stu-id="e3f50-111">Add or remove ACL entries from the <xref:System.Security.AccessControl.DirectorySecurity> object returned from step 1.</span></span>  
  
3. <span data-ttu-id="e3f50-112">Chcete-li použít změny, předajte <xref:System.Security.AccessControl.DirectorySecurity> objekt metodě. <xref:System.IO.Directory.SetAccessControl%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="e3f50-112">To apply the changes, pass the <xref:System.Security.AccessControl.DirectorySecurity> object to the <xref:System.IO.Directory.SetAccessControl%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3f50-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="e3f50-113">Example</span></span>  
 <span data-ttu-id="e3f50-114">Ke spuštění tohoto příkladu je nutné použít platný uživatelský nebo skupinový účet.</span><span class="sxs-lookup"><span data-stu-id="e3f50-114">You must use a valid user or group account to run this example.</span></span> <span data-ttu-id="e3f50-115">Příklad používá <xref:System.IO.File> objekt.</span><span class="sxs-lookup"><span data-stu-id="e3f50-115">The example uses a <xref:System.IO.File> object.</span></span> <span data-ttu-id="e3f50-116">Použijte stejný postup <xref:System.IO.FileInfo>pro <xref:System.IO.Directory>, <xref:System.IO.DirectoryInfo> a třídy.</span><span class="sxs-lookup"><span data-stu-id="e3f50-116">Use the same procedure for the <xref:System.IO.FileInfo>, <xref:System.IO.Directory>, and <xref:System.IO.DirectoryInfo> classes.</span></span>

 [!code-csharp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/CS/sample.cs#1)]
 [!code-vb[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/VB/sample.vb#1)]  
