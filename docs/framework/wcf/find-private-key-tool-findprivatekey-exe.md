---
title: Nástroj pro hledání soukromého klíče (FindPrivateKey.exe)
ms.date: 09/11/2017
ms.assetid: b8846a95-3fcc-4e8c-b9c0-128d975a6307
ms.openlocfilehash: 316f55b93cf4d867b99878bf483b73cb3f09ad04
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990356"
---
# <a name="find-private-key-tool-findprivatekeyexe"></a><span data-ttu-id="fea9d-102">Nástroj pro hledání soukromého klíče (FindPrivateKey.exe)</span><span class="sxs-lookup"><span data-stu-id="fea9d-102">Find Private Key Tool (FindPrivateKey.exe)</span></span>

<span data-ttu-id="fea9d-103">Tento nástroj příkazového řádku je možné použít k načtení privátního klíče z úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="fea9d-103">This command-line tool can be used to retrieve a private key from a certificate store.</span></span> <span data-ttu-id="fea9d-104">Například *FindPrivateKey. exe* lze použít k vyhledání umístění a názvu souboru privátního klíče přidruženého k určitému certifikátu X. 509 v úložišti certifikátů.</span><span class="sxs-lookup"><span data-stu-id="fea9d-104">For example, *FindPrivateKey.exe* can be used to find the location and name of the private key file associated with a specific X.509 certificate in the certificate store.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fea9d-105">Nástroj FindPrivateKey se dodává jako ukázka WCF.</span><span class="sxs-lookup"><span data-stu-id="fea9d-105">The FindPrivateKey tool is shipped as a WCF sample.</span></span> <span data-ttu-id="fea9d-106">Další informace o tom, kde najít ukázku a jak ji sestavit, najdete v tématu [FindPrivateKey](./samples/findprivatekey.md).</span><span class="sxs-lookup"><span data-stu-id="fea9d-106">For more information about where to find the sample and how to build it, see [FindPrivateKey](./samples/findprivatekey.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="fea9d-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fea9d-107">Syntax</span></span>

```console
FindPrivateKey<storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]
```

## <a name="remarks"></a><span data-ttu-id="fea9d-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fea9d-108">Remarks</span></span>

<span data-ttu-id="fea9d-109">Následující tabulky popisují argumenty a možnosti, které lze použít pomocí nástroje najít privátní klíč (FindPrivateKey. exe).</span><span class="sxs-lookup"><span data-stu-id="fea9d-109">The following tables describe the arguments and the options that can be used with the Find Private Key tool (FindPrivateKey.exe).</span></span>

|<span data-ttu-id="fea9d-110">Argument</span><span class="sxs-lookup"><span data-stu-id="fea9d-110">Argument</span></span>|<span data-ttu-id="fea9d-111">Popis</span><span class="sxs-lookup"><span data-stu-id="fea9d-111">Description</span></span>|
|--------------|-----------------|
|`storeName`|<span data-ttu-id="fea9d-112">Název úložiště certifikátů</span><span class="sxs-lookup"><span data-stu-id="fea9d-112">Name of the certificate store.</span></span>|
|`storeLocation`|<span data-ttu-id="fea9d-113">Umístění úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="fea9d-113">The location of the certificate store.</span></span>|

|<span data-ttu-id="fea9d-114">Možnost</span><span class="sxs-lookup"><span data-stu-id="fea9d-114">Option</span></span>|<span data-ttu-id="fea9d-115">Popis</span><span class="sxs-lookup"><span data-stu-id="fea9d-115">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="fea9d-116">`/n <`*Subject*`>`</span><span class="sxs-lookup"><span data-stu-id="fea9d-116">`/n <` *subjectName* `>`</span></span>|<span data-ttu-id="fea9d-117">Určuje název subjektu certifikátu.</span><span class="sxs-lookup"><span data-stu-id="fea9d-117">Specifies the subject name of the certificate.</span></span>|
|<span data-ttu-id="fea9d-118">`/t <`*kryptografický otisk*`>`</span><span class="sxs-lookup"><span data-stu-id="fea9d-118">`/t <` *thumbprint* `>`</span></span>|<span data-ttu-id="fea9d-119">Určuje kryptografický otisk certifikátu.</span><span class="sxs-lookup"><span data-stu-id="fea9d-119">Specifies the thumbprint of the certificate.</span></span> <span data-ttu-id="fea9d-120">K načtení kryptografického otisku certifikátu použijte soubor certmgr. exe.</span><span class="sxs-lookup"><span data-stu-id="fea9d-120">Use Certmgr.exe to retrieve the thumbprint of the certificate.</span></span>|
|`/f`|<span data-ttu-id="fea9d-121">Vypíše pouze název souboru.</span><span class="sxs-lookup"><span data-stu-id="fea9d-121">Outputs the file name only.</span></span>|
|`/d`|<span data-ttu-id="fea9d-122">Vypíše pouze adresář.</span><span class="sxs-lookup"><span data-stu-id="fea9d-122">Outputs the directory only.</span></span>|
|`/a`|<span data-ttu-id="fea9d-123">Vypíše absolutní název souboru.</span><span class="sxs-lookup"><span data-stu-id="fea9d-123">Outputs the absolute file name.</span></span>|

## <a name="examples"></a><span data-ttu-id="fea9d-124">Příklady</span><span class="sxs-lookup"><span data-stu-id="fea9d-124">Examples</span></span>

<span data-ttu-id="fea9d-125">Následující příkaz načte privátní klíč pro Jan Karásek:</span><span class="sxs-lookup"><span data-stu-id="fea9d-125">The following command retrieves the private key for John Doe:</span></span>

```console
FindPrivateKey My CurrentUser -n "CN=John Doe"
```

<span data-ttu-id="fea9d-126">Následující příkaz načte privátní klíč pro místní počítač:</span><span class="sxs-lookup"><span data-stu-id="fea9d-126">The following command retrieves the private key for the local machine:</span></span>

```console
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" –a
```
