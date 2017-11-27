---
title: "Nástroj pro hledání soukromého klíče (FindPrivateKey.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b8846a95-3fcc-4e8c-b9c0-128d975a6307
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5e2110e129b293ffb04c8e3eb69a5c3bfe83c17b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="find-private-key-tool-findprivatekeyexe"></a><span data-ttu-id="027a5-102">Nástroj pro hledání soukromého klíče (FindPrivateKey.exe)</span><span class="sxs-lookup"><span data-stu-id="027a5-102">Find Private Key Tool (FindPrivateKey.exe)</span></span>
<span data-ttu-id="027a5-103">Tento nástroj příkazového řádku lze získat privátní klíč z úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="027a5-103">This command-line tool can be used to retrieve a private key from a certificate store.</span></span> <span data-ttu-id="027a5-104">FindPrivateKey.exe můžete například použít k vyhledání umístění a název souboru privátního klíče přidruženého k určité X.509 certifikátu v úložišti certifikátů.</span><span class="sxs-lookup"><span data-stu-id="027a5-104">For example, FindPrivateKey.exe can be used to find the location and name of the private key file associated with a specific X.509 certificate in the certificate store.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="027a5-105">Nástroj FindPrivateKey je dodávána jako Ukázka WCF.</span><span class="sxs-lookup"><span data-stu-id="027a5-105">The FindPrivateKey tool is shipped as a WCF sample.</span></span> <span data-ttu-id="027a5-106">Další informace o tom, kde najít ukázky a jak vytvořit, najdete v části</span><span class="sxs-lookup"><span data-stu-id="027a5-106">For more information about where to find the sample and how to build it, see</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="027a5-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="027a5-107">Syntax</span></span>  
  
```  
FindPrivateKey<storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]  
```  
  
## <a name="remarks"></a><span data-ttu-id="027a5-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="027a5-108">Remarks</span></span>  
 <span data-ttu-id="027a5-109">Následující tabulky popisují argumenty a možnosti, které je možné pomocí nástroje Najít privátního klíče (FindPrivateKey.exe).</span><span class="sxs-lookup"><span data-stu-id="027a5-109">The following tables describe the arguments and the options that can be used with the Find Private Key tool (FindPrivateKey.exe).</span></span>  
  
|<span data-ttu-id="027a5-110">Argument</span><span class="sxs-lookup"><span data-stu-id="027a5-110">Argument</span></span>|<span data-ttu-id="027a5-111">Popis</span><span class="sxs-lookup"><span data-stu-id="027a5-111">Description</span></span>|  
|--------------|-----------------|  
|`storeName`|<span data-ttu-id="027a5-112">Název úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="027a5-112">Name of the certificate store.</span></span>|  
|`storeLocation`|<span data-ttu-id="027a5-113">Umístění úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="027a5-113">The location of the certificate store.</span></span>|  
  
|<span data-ttu-id="027a5-114">Možnost</span><span class="sxs-lookup"><span data-stu-id="027a5-114">Option</span></span>|<span data-ttu-id="027a5-115">Popis</span><span class="sxs-lookup"><span data-stu-id="027a5-115">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="027a5-116">`/n <`*subjectName*`>`</span><span class="sxs-lookup"><span data-stu-id="027a5-116">`/n <` *subjectName* `>`</span></span>|<span data-ttu-id="027a5-117">Určuje název předmětu certifikátu.</span><span class="sxs-lookup"><span data-stu-id="027a5-117">Specifies the subject name of the certificate.</span></span>|  
|<span data-ttu-id="027a5-118">`/t <`*kryptografický otisk*`>`</span><span class="sxs-lookup"><span data-stu-id="027a5-118">`/t <` *thumbprint* `>`</span></span>|<span data-ttu-id="027a5-119">Určuje kryptografický otisk certifikátu.</span><span class="sxs-lookup"><span data-stu-id="027a5-119">Specifies the thumbprint of the certificate.</span></span> <span data-ttu-id="027a5-120">Pomocí Certmgr.exe získat kryptografický otisk certifikátu.</span><span class="sxs-lookup"><span data-stu-id="027a5-120">Use Certmgr.exe to retrieve the thumbprint of the certificate.</span></span>|  
|`/f`|<span data-ttu-id="027a5-121">Výstupy pouze název souboru.</span><span class="sxs-lookup"><span data-stu-id="027a5-121">Outputs the file name only.</span></span>|  
|`/d`|<span data-ttu-id="027a5-122">Výstupy pouze adresáři.</span><span class="sxs-lookup"><span data-stu-id="027a5-122">Outputs the directory only.</span></span>|  
|`/a`|<span data-ttu-id="027a5-123">Výstupy název souboru na absolutní.</span><span class="sxs-lookup"><span data-stu-id="027a5-123">Outputs the absolute file name.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="027a5-124">Příklady</span><span class="sxs-lookup"><span data-stu-id="027a5-124">Examples</span></span>  
 <span data-ttu-id="027a5-125">Tento příkaz načte privátní klíč pro John Doe.</span><span class="sxs-lookup"><span data-stu-id="027a5-125">The following command retrieves the private key for John Doe.</span></span>  
  
```  
FindPrivateKey My CurrentUser -n "CN=John Doe"  
```  
  
 <span data-ttu-id="027a5-126">Tento příkaz načte privátní klíč pro místní počítač.</span><span class="sxs-lookup"><span data-stu-id="027a5-126">The following command retrieves the private key for the local machine.</span></span>  
  
```  
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" –a  
```
