---
title: Cert2spc.exe (nástroj pro testování certifikátu vydavatele softwaru)
ms.date: 03/30/2017
helpviewer_keywords:
- SPC
- Software Publisher Certificate Test tool
- Software Publisher Certificate
- Cert2spc.exe
- certificates, Software Publisher's Certificate
ms.assetid: be434d7d-9c0d-46e7-8392-58a9b542d11d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49a5ad951c47100199c93d03efb07ffc6fda5080
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70851413"
---
# <a name="cert2spcexe-software-publisher-certificate-test-tool"></a><span data-ttu-id="efc62-102">Cert2spc.exe (nástroj pro testování certifikátu vydavatele softwaru)</span><span class="sxs-lookup"><span data-stu-id="efc62-102">Cert2spc.exe (Software Publisher Certificate Test Tool)</span></span>
<span data-ttu-id="efc62-103">Nástroj Software Publisher Certificate Test vytvoří certifikát Software Publisher's Certificate (SPC) z jednoho nebo více certifikátů X.509.</span><span class="sxs-lookup"><span data-stu-id="efc62-103">The Software Publisher Certificate Test tool creates a Software Publisher's Certificate (SPC) from one or more X.509 certificates.</span></span> <span data-ttu-id="efc62-104">Nástroj Cert2spc.exe slouží pouze k testování.</span><span class="sxs-lookup"><span data-stu-id="efc62-104">Cert2spc.exe is for test purposes only.</span></span> <span data-ttu-id="efc62-105">Platný certifikát SPC lze získat od certifikačního úřadu, například VeriSign nebo Thawte.</span><span class="sxs-lookup"><span data-stu-id="efc62-105">You can obtain a valid SPC from a Certification Authority such as VeriSign or Thawte.</span></span> <span data-ttu-id="efc62-106">Další informace o vytváření certifikátů X. 509 najdete v tématu [Makecert. exe (Nástroj pro vytváření certifikátů)](/windows/desktop/SecCrypto/makecert).</span><span class="sxs-lookup"><span data-stu-id="efc62-106">For more information about creating X.509 certificates, see [Makecert.exe (Certificate Creation Tool)](/windows/desktop/SecCrypto/makecert).</span></span>  
  
 <span data-ttu-id="efc62-107">Tento nástroj je automaticky nainstalován se sadou Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="efc62-107">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="efc62-108">Chcete-li spustit nástroj, použijte Developer Command Prompt pro Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7).</span><span class="sxs-lookup"><span data-stu-id="efc62-108">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="efc62-109">Další informace najdete v tématu [výzvy k zadání příkazu](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="efc62-109">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="efc62-110">V příkazovém řádku zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="efc62-110">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efc62-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="efc62-111">Syntax</span></span>  
  
```console  
cert2spc cert1.cer | crl1.crl [... certN.cer | crlN.crl] outputSPCfile.spc  
```  
  
## <a name="parameters"></a><span data-ttu-id="efc62-112">Parametry</span><span class="sxs-lookup"><span data-stu-id="efc62-112">Parameters</span></span>  
  
|<span data-ttu-id="efc62-113">Argument</span><span class="sxs-lookup"><span data-stu-id="efc62-113">Argument</span></span>|<span data-ttu-id="efc62-114">Popis</span><span class="sxs-lookup"><span data-stu-id="efc62-114">Description</span></span>|  
|--------------|-----------------|  
|`certN.cer`|<span data-ttu-id="efc62-115">Název certifikátu X.509, který má být zahrnut do souboru SPC.</span><span class="sxs-lookup"><span data-stu-id="efc62-115">The name of an X.509 certificate to include in the SPC file.</span></span> <span data-ttu-id="efc62-116">Můžete zadat více názvů oddělených mezerami.</span><span class="sxs-lookup"><span data-stu-id="efc62-116">You can specify multiple names separated by spaces.</span></span>|  
|`crlN.crl`|<span data-ttu-id="efc62-117">Název seznamu odvolání certifikátu, který má být zahrnut do souboru SPC.</span><span class="sxs-lookup"><span data-stu-id="efc62-117">The name of a certificate revocation list to include in the SPC file.</span></span> <span data-ttu-id="efc62-118">Můžete zadat více názvů oddělených mezerami.</span><span class="sxs-lookup"><span data-stu-id="efc62-118">You can specify multiple names separated by spaces.</span></span>|  
|`outputSPCfile.spc`|<span data-ttu-id="efc62-119">Název objektu PKCS #7, který bude obsahovat certifikáty X.509.</span><span class="sxs-lookup"><span data-stu-id="efc62-119">The name of the PKCS #7 object that will contain the X.509 certificates.</span></span>|  
  
|<span data-ttu-id="efc62-120">Možnost</span><span class="sxs-lookup"><span data-stu-id="efc62-120">Option</span></span>|<span data-ttu-id="efc62-121">Popis</span><span class="sxs-lookup"><span data-stu-id="efc62-121">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="efc62-122">**/?**</span><span class="sxs-lookup"><span data-stu-id="efc62-122">**/?**</span></span>|<span data-ttu-id="efc62-123">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="efc62-123">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="efc62-124">Příklady</span><span class="sxs-lookup"><span data-stu-id="efc62-124">Examples</span></span>  
 <span data-ttu-id="efc62-125">Následující příkaz vytvoří SPC z `myCertificate.cer` a umístí ho do. `mySPCFile.spc`</span><span class="sxs-lookup"><span data-stu-id="efc62-125">The following command creates an SPC from `myCertificate.cer` and places it in `mySPCFile.spc`.</span></span>  
  
```console
cert2spc myCertificate.cer mySPCFile.spc  
```  
  
 <span data-ttu-id="efc62-126">Následující příkaz vytvoří SPC z `oneCertificate.cer` a `twoCertificate.cer`a umístí ho do `mySPCFile.spc`.</span><span class="sxs-lookup"><span data-stu-id="efc62-126">The following command creates an SPC from `oneCertificate.cer` and `twoCertificate.cer`, and places it in `mySPCFile.spc`.</span></span>  
  
```console
cert2spc oneCertificate.cer twoCertificate.cer mySPCFile.spc  
```  
  
## <a name="see-also"></a><span data-ttu-id="efc62-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="efc62-127">See also</span></span>

- [<span data-ttu-id="efc62-128">Nástroje</span><span class="sxs-lookup"><span data-stu-id="efc62-128">Tools</span></span>](../../../docs/framework/tools/index.md)
- [<span data-ttu-id="efc62-129">Makecert. exe (Nástroj pro vytvoření certifikátu)</span><span class="sxs-lookup"><span data-stu-id="efc62-129">Makecert.exe (Certificate Creation Tool)</span></span>](/windows/desktop/SecCrypto/makecert)
- [<span data-ttu-id="efc62-130">Příkazové řádky</span><span class="sxs-lookup"><span data-stu-id="efc62-130">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
