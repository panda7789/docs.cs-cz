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
# <a name="how-to-add-or-remove-access-control-list-entries-net-framework-only"></a><span data-ttu-id="b4f2f-102">Postupy: přidávání a odebírání položek seznamu Access Control (pouze .NET Framework)</span><span class="sxs-lookup"><span data-stu-id="b4f2f-102">How to: Add or remove Access Control List entries (.NET Framework only)</span></span>
<span data-ttu-id="b4f2f-103">Chcete-li přidat nebo odebrat položky seznamu Access Control (seznam ACL) do souboru nebo adresáře nebo z něj, získejte objekt <xref:System.Security.AccessControl.FileSecurity> nebo <xref:System.Security.AccessControl.DirectorySecurity> ze souboru nebo adresáře.</span><span class="sxs-lookup"><span data-stu-id="b4f2f-103">To add or remove Access Control List (ACL) entries to or from a file or directory, get the <xref:System.Security.AccessControl.FileSecurity> or <xref:System.Security.AccessControl.DirectorySecurity> object from the file or directory.</span></span> <span data-ttu-id="b4f2f-104">Upravte objekt a pak ho použijte zpátky do souboru nebo adresáře.</span><span class="sxs-lookup"><span data-stu-id="b4f2f-104">Modify the object, and then apply it back to the file or directory.</span></span>  
  
## <a name="add-or-remove-an-acl-entry-from-a-file"></a><span data-ttu-id="b4f2f-105">Přidat nebo odebrat položku seznamu řízení přístupu (ACL) ze souboru</span><span class="sxs-lookup"><span data-stu-id="b4f2f-105">Add or remove an ACL entry from a file</span></span>  
  
1. <span data-ttu-id="b4f2f-106">Voláním metody <xref:System.IO.File.GetAccessControl%2A?displayProperty=nameWithType> získáte objekt <xref:System.Security.AccessControl.FileSecurity>, který obsahuje aktuální položky seznamu ACL souboru.</span><span class="sxs-lookup"><span data-stu-id="b4f2f-106">Call the <xref:System.IO.File.GetAccessControl%2A?displayProperty=nameWithType> method to get a <xref:System.Security.AccessControl.FileSecurity> object that contains the current ACL entries of a file.</span></span>  
  
2. <span data-ttu-id="b4f2f-107">Přidá nebo odebere položky seznamu řízení přístupu z objektu <xref:System.Security.AccessControl.FileSecurity> vráceného z kroku 1.</span><span class="sxs-lookup"><span data-stu-id="b4f2f-107">Add or remove ACL entries from the <xref:System.Security.AccessControl.FileSecurity> object returned from step 1.</span></span>  
  
3. <span data-ttu-id="b4f2f-108">Chcete-li použít změny, předejte objekt <xref:System.Security.AccessControl.FileSecurity> do metody <xref:System.IO.File.SetAccessControl%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b4f2f-108">To apply the changes, pass the <xref:System.Security.AccessControl.FileSecurity> object to the <xref:System.IO.File.SetAccessControl%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="add-or-remove-an-acl-entry-from-a-directory"></a><span data-ttu-id="b4f2f-109">Přidat nebo odebrat položku seznamu řízení přístupu (ACL) z adresáře</span><span class="sxs-lookup"><span data-stu-id="b4f2f-109">Add or remove an ACL entry from a directory</span></span>  
  
1. <span data-ttu-id="b4f2f-110">Voláním metody <xref:System.IO.Directory.GetAccessControl%2A?displayProperty=nameWithType> získáte objekt <xref:System.Security.AccessControl.DirectorySecurity>, který obsahuje aktuální položky seznamu ACL adresáře.</span><span class="sxs-lookup"><span data-stu-id="b4f2f-110">Call the <xref:System.IO.Directory.GetAccessControl%2A?displayProperty=nameWithType> method to get a <xref:System.Security.AccessControl.DirectorySecurity> object that contains the current ACL entries of a directory.</span></span>  
  
2. <span data-ttu-id="b4f2f-111">Přidá nebo odebere položky seznamu řízení přístupu z objektu <xref:System.Security.AccessControl.DirectorySecurity> vráceného z kroku 1.</span><span class="sxs-lookup"><span data-stu-id="b4f2f-111">Add or remove ACL entries from the <xref:System.Security.AccessControl.DirectorySecurity> object returned from step 1.</span></span>  
  
3. <span data-ttu-id="b4f2f-112">Chcete-li použít změny, předejte objekt <xref:System.Security.AccessControl.DirectorySecurity> do metody <xref:System.IO.Directory.SetAccessControl%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b4f2f-112">To apply the changes, pass the <xref:System.Security.AccessControl.DirectorySecurity> object to the <xref:System.IO.Directory.SetAccessControl%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b4f2f-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="b4f2f-113">Example</span></span>  
 <span data-ttu-id="b4f2f-114">Chcete-li spustit tento příklad, je nutné použít platný účet uživatele nebo skupiny.</span><span class="sxs-lookup"><span data-stu-id="b4f2f-114">You must use a valid user or group account to run this example.</span></span> <span data-ttu-id="b4f2f-115">V příkladu se používá objekt <xref:System.IO.File>.</span><span class="sxs-lookup"><span data-stu-id="b4f2f-115">The example uses a <xref:System.IO.File> object.</span></span> <span data-ttu-id="b4f2f-116">Pro třídy <xref:System.IO.FileInfo>, <xref:System.IO.Directory>a <xref:System.IO.DirectoryInfo> použijte stejný postup.</span><span class="sxs-lookup"><span data-stu-id="b4f2f-116">Use the same procedure for the <xref:System.IO.FileInfo>, <xref:System.IO.Directory>, and <xref:System.IO.DirectoryInfo> classes.</span></span>

 [!code-csharp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/CS/sample.cs#1)]
 [!code-vb[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/VB/sample.vb#1)]  
