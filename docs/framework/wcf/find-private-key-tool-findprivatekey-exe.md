---
title: Nástroj pro hledání soukromého klíče (FindPrivateKey.exe)
ms.date: 09/11/2017
ms.assetid: b8846a95-3fcc-4e8c-b9c0-128d975a6307
ms.openlocfilehash: 8f156cbb2f4fad8d51e356bd4dee2d72d9397ffb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61929581"
---
# <a name="find-private-key-tool-findprivatekeyexe"></a><span data-ttu-id="de4bb-102">Nástroj pro hledání soukromého klíče (FindPrivateKey.exe)</span><span class="sxs-lookup"><span data-stu-id="de4bb-102">Find Private Key Tool (FindPrivateKey.exe)</span></span>

<span data-ttu-id="de4bb-103">Tento nástroj příkazového řádku je možné načíst privátní klíč z úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="de4bb-103">This command-line tool can be used to retrieve a private key from a certificate store.</span></span> <span data-ttu-id="de4bb-104">Například *FindPrivateKey.exe* slouží k vyhledání umístění a název souboru privátního klíče přidružené k určité certifikát X.509 v úložišti certifikátů.</span><span class="sxs-lookup"><span data-stu-id="de4bb-104">For example, *FindPrivateKey.exe* can be used to find the location and name of the private key file associated with a specific X.509 certificate in the certificate store.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="de4bb-105">Nástroj FindPrivateKey je dodáván jako ukázku WCF.</span><span class="sxs-lookup"><span data-stu-id="de4bb-105">The FindPrivateKey tool is shipped as a WCF sample.</span></span> <span data-ttu-id="de4bb-106">Další informace o kde najít ukázky a jak ji sestavit, naleznete v tématu [FindPrivateKey](./samples/findprivatekey.md).</span><span class="sxs-lookup"><span data-stu-id="de4bb-106">For more information about where to find the sample and how to build it, see [FindPrivateKey](./samples/findprivatekey.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="de4bb-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="de4bb-107">Syntax</span></span>

```
FindPrivateKey<storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]
```

## <a name="remarks"></a><span data-ttu-id="de4bb-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="de4bb-108">Remarks</span></span>

<span data-ttu-id="de4bb-109">Následující tabulky popisují argumenty a možnosti, které je možné pomocí nástroje pro hledání privátního klíče (FindPrivateKey.exe).</span><span class="sxs-lookup"><span data-stu-id="de4bb-109">The following tables describe the arguments and the options that can be used with the Find Private Key tool (FindPrivateKey.exe).</span></span>

|<span data-ttu-id="de4bb-110">Argument</span><span class="sxs-lookup"><span data-stu-id="de4bb-110">Argument</span></span>|<span data-ttu-id="de4bb-111">Popis</span><span class="sxs-lookup"><span data-stu-id="de4bb-111">Description</span></span>|
|--------------|-----------------|
|`storeName`|<span data-ttu-id="de4bb-112">Název úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="de4bb-112">Name of the certificate store.</span></span>|
|`storeLocation`|<span data-ttu-id="de4bb-113">Umístění úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="de4bb-113">The location of the certificate store.</span></span>|

|<span data-ttu-id="de4bb-114">Možnost</span><span class="sxs-lookup"><span data-stu-id="de4bb-114">Option</span></span>|<span data-ttu-id="de4bb-115">Popis</span><span class="sxs-lookup"><span data-stu-id="de4bb-115">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="de4bb-116">`/n <` *subjectName* `>`</span><span class="sxs-lookup"><span data-stu-id="de4bb-116">`/n <` *subjectName* `>`</span></span>|<span data-ttu-id="de4bb-117">Určuje název subjektu certifikátu.</span><span class="sxs-lookup"><span data-stu-id="de4bb-117">Specifies the subject name of the certificate.</span></span>|
|<span data-ttu-id="de4bb-118">`/t <` *Kryptografický otisk* `>`</span><span class="sxs-lookup"><span data-stu-id="de4bb-118">`/t <` *thumbprint* `>`</span></span>|<span data-ttu-id="de4bb-119">Určuje kryptografický otisk certifikátu.</span><span class="sxs-lookup"><span data-stu-id="de4bb-119">Specifies the thumbprint of the certificate.</span></span> <span data-ttu-id="de4bb-120">Certmgr.exe slouží k načtení kryptografického otisku certifikátu.</span><span class="sxs-lookup"><span data-stu-id="de4bb-120">Use Certmgr.exe to retrieve the thumbprint of the certificate.</span></span>|
|`/f`|<span data-ttu-id="de4bb-121">Vypíše pouze název souboru.</span><span class="sxs-lookup"><span data-stu-id="de4bb-121">Outputs the file name only.</span></span>|
|`/d`|<span data-ttu-id="de4bb-122">Vypíše pouze adresáře.</span><span class="sxs-lookup"><span data-stu-id="de4bb-122">Outputs the directory only.</span></span>|
|`/a`|<span data-ttu-id="de4bb-123">Výstupem absolutní název souboru.</span><span class="sxs-lookup"><span data-stu-id="de4bb-123">Outputs the absolute file name.</span></span>|

## <a name="examples"></a><span data-ttu-id="de4bb-124">Příklady</span><span class="sxs-lookup"><span data-stu-id="de4bb-124">Examples</span></span>

<span data-ttu-id="de4bb-125">Následující příkaz načte privátní klíč pro John Doe:</span><span class="sxs-lookup"><span data-stu-id="de4bb-125">The following command retrieves the private key for John Doe:</span></span>

```
FindPrivateKey My CurrentUser -n "CN=John Doe"
```

<span data-ttu-id="de4bb-126">Následující příkaz načte privátní klíč pro místní počítač:</span><span class="sxs-lookup"><span data-stu-id="de4bb-126">The following command retrieves the private key for the local machine:</span></span>

```
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" –a
```