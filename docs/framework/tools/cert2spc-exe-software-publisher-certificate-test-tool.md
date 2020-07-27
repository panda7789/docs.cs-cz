---
title: Cert2spc.exe (nástroj pro testování certifikátu vydavatele softwaru)
description: Použijte Cert2spc.exe Nástroj pro testování certifikátu vydavatele softwaru. Tento nástroj vytvoří certifikát vydavatele softwaru (SPC) z jednoho nebo více certifikátů X. 509.
ms.date: 03/30/2017
helpviewer_keywords:
- SPC
- Software Publisher Certificate Test tool
- Software Publisher Certificate
- Cert2spc.exe
- certificates, Software Publisher's Certificate
ms.assetid: be434d7d-9c0d-46e7-8392-58a9b542d11d
ms.openlocfilehash: 2eb6339aa6f5d23a5b87986410cbeaac2dac2bec
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167321"
---
# <a name="cert2spcexe-software-publisher-certificate-test-tool"></a><span data-ttu-id="1dcd0-104">Cert2spc.exe (nástroj pro testování certifikátu vydavatele softwaru)</span><span class="sxs-lookup"><span data-stu-id="1dcd0-104">Cert2spc.exe (Software Publisher Certificate Test Tool)</span></span>
<span data-ttu-id="1dcd0-105">Nástroj Software Publisher Certificate Test vytvoří certifikát Software Publisher's Certificate (SPC) z jednoho nebo více certifikátů X.509.</span><span class="sxs-lookup"><span data-stu-id="1dcd0-105">The Software Publisher Certificate Test tool creates a Software Publisher's Certificate (SPC) from one or more X.509 certificates.</span></span> <span data-ttu-id="1dcd0-106">Nástroj Cert2spc.exe slouží pouze k testování.</span><span class="sxs-lookup"><span data-stu-id="1dcd0-106">Cert2spc.exe is for test purposes only.</span></span> <span data-ttu-id="1dcd0-107">Platný certifikát SPC lze získat od certifikačního úřadu, například VeriSign nebo Thawte.</span><span class="sxs-lookup"><span data-stu-id="1dcd0-107">You can obtain a valid SPC from a Certification Authority such as VeriSign or Thawte.</span></span> <span data-ttu-id="1dcd0-108">Další informace o vytváření certifikátů X. 509 najdete v tématu [Makecert.exe (Nástroj pro vytváření certifikátů)](/windows/desktop/SecCrypto/makecert).</span><span class="sxs-lookup"><span data-stu-id="1dcd0-108">For more information about creating X.509 certificates, see [Makecert.exe (Certificate Creation Tool)](/windows/desktop/SecCrypto/makecert).</span></span>  
  
 <span data-ttu-id="1dcd0-109">Tento nástroj je automaticky nainstalován se sadou Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1dcd0-109">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="1dcd0-110">Chcete-li spustit nástroj, použijte Developer Command Prompt pro Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7).</span><span class="sxs-lookup"><span data-stu-id="1dcd0-110">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="1dcd0-111">Další informace najdete v tématu [výzvy k zadání příkazu](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="1dcd0-111">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="1dcd0-112">V příkazovém řádku zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="1dcd0-112">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1dcd0-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1dcd0-113">Syntax</span></span>  
  
```console  
cert2spc cert1.cer | crl1.crl [... certN.cer | crlN.crl] outputSPCfile.spc  
```  
  
## <a name="parameters"></a><span data-ttu-id="1dcd0-114">Parametry</span><span class="sxs-lookup"><span data-stu-id="1dcd0-114">Parameters</span></span>  
  
|<span data-ttu-id="1dcd0-115">Argument</span><span class="sxs-lookup"><span data-stu-id="1dcd0-115">Argument</span></span>|<span data-ttu-id="1dcd0-116">Popis</span><span class="sxs-lookup"><span data-stu-id="1dcd0-116">Description</span></span>|  
|--------------|-----------------|  
|`certN.cer`|<span data-ttu-id="1dcd0-117">Název certifikátu X.509, který má být zahrnut do souboru SPC.</span><span class="sxs-lookup"><span data-stu-id="1dcd0-117">The name of an X.509 certificate to include in the SPC file.</span></span> <span data-ttu-id="1dcd0-118">Můžete zadat více názvů oddělených mezerami.</span><span class="sxs-lookup"><span data-stu-id="1dcd0-118">You can specify multiple names separated by spaces.</span></span>|  
|`crlN.crl`|<span data-ttu-id="1dcd0-119">Název seznamu odvolání certifikátu, který má být zahrnut do souboru SPC.</span><span class="sxs-lookup"><span data-stu-id="1dcd0-119">The name of a certificate revocation list to include in the SPC file.</span></span> <span data-ttu-id="1dcd0-120">Můžete zadat více názvů oddělených mezerami.</span><span class="sxs-lookup"><span data-stu-id="1dcd0-120">You can specify multiple names separated by spaces.</span></span>|  
|`outputSPCfile.spc`|<span data-ttu-id="1dcd0-121">Název objektu PKCS #7, který bude obsahovat certifikáty X.509.</span><span class="sxs-lookup"><span data-stu-id="1dcd0-121">The name of the PKCS #7 object that will contain the X.509 certificates.</span></span>|  
  
|<span data-ttu-id="1dcd0-122">Možnost</span><span class="sxs-lookup"><span data-stu-id="1dcd0-122">Option</span></span>|<span data-ttu-id="1dcd0-123">Popis</span><span class="sxs-lookup"><span data-stu-id="1dcd0-123">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="1dcd0-124">**/?**</span><span class="sxs-lookup"><span data-stu-id="1dcd0-124">**/?**</span></span>|<span data-ttu-id="1dcd0-125">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="1dcd0-125">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="1dcd0-126">Příklady</span><span class="sxs-lookup"><span data-stu-id="1dcd0-126">Examples</span></span>  
 <span data-ttu-id="1dcd0-127">Následující příkaz vytvoří SPC z `myCertificate.cer` a umístí ho do `mySPCFile.spc` .</span><span class="sxs-lookup"><span data-stu-id="1dcd0-127">The following command creates an SPC from `myCertificate.cer` and places it in `mySPCFile.spc`.</span></span>  
  
```console
cert2spc myCertificate.cer mySPCFile.spc  
```  
  
 <span data-ttu-id="1dcd0-128">Následující příkaz vytvoří SPC z a a `oneCertificate.cer` `twoCertificate.cer` umístí ho do `mySPCFile.spc` .</span><span class="sxs-lookup"><span data-stu-id="1dcd0-128">The following command creates an SPC from `oneCertificate.cer` and `twoCertificate.cer`, and places it in `mySPCFile.spc`.</span></span>  
  
```console
cert2spc oneCertificate.cer twoCertificate.cer mySPCFile.spc  
```  
  
## <a name="see-also"></a><span data-ttu-id="1dcd0-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="1dcd0-129">See also</span></span>

- [<span data-ttu-id="1dcd0-130">Nástroje</span><span class="sxs-lookup"><span data-stu-id="1dcd0-130">Tools</span></span>](index.md)
- [<span data-ttu-id="1dcd0-131">Makecert.exe (Nástroj pro vytvoření certifikátu)</span><span class="sxs-lookup"><span data-stu-id="1dcd0-131">Makecert.exe (Certificate Creation Tool)</span></span>](/windows/desktop/SecCrypto/makecert)
- [<span data-ttu-id="1dcd0-132">Výzvy příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="1dcd0-132">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
