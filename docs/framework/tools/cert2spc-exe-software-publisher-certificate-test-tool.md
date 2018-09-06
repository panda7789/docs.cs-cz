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
ms.openlocfilehash: 5b0ef0072e6e9a1e9f4a28d6e19894f301fe3fc0
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43864797"
---
# <a name="cert2spcexe-software-publisher-certificate-test-tool"></a><span data-ttu-id="ec656-102">Cert2spc.exe (nástroj pro testování certifikátu vydavatele softwaru)</span><span class="sxs-lookup"><span data-stu-id="ec656-102">Cert2spc.exe (Software Publisher Certificate Test Tool)</span></span>
<span data-ttu-id="ec656-103">Nástroj Software Publisher Certificate Test vytvoří certifikát Software Publisher's Certificate (SPC) z jednoho nebo více certifikátů X.509.</span><span class="sxs-lookup"><span data-stu-id="ec656-103">The Software Publisher Certificate Test tool creates a Software Publisher's Certificate (SPC) from one or more X.509 certificates.</span></span> <span data-ttu-id="ec656-104">Nástroj Cert2spc.exe slouží pouze k testování.</span><span class="sxs-lookup"><span data-stu-id="ec656-104">Cert2spc.exe is for test purposes only.</span></span> <span data-ttu-id="ec656-105">Platný certifikát SPC lze získat od certifikačního úřadu, například VeriSign nebo Thawte.</span><span class="sxs-lookup"><span data-stu-id="ec656-105">You can obtain a valid SPC from a Certification Authority such as VeriSign or Thawte.</span></span> <span data-ttu-id="ec656-106">Další informace o vytváření certifikátů X.509 naleznete v tématu [Makecert.exe (Certificate Creation Tool)](https://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d).</span><span class="sxs-lookup"><span data-stu-id="ec656-106">For more information about creating X.509 certificates, see [Makecert.exe (Certificate Creation Tool)](https://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d).</span></span>  
  
 <span data-ttu-id="ec656-107">Tento nástroj je automaticky nainstalován se sadou Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ec656-107">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="ec656-108">Chcete-li spustit tento nástroj, použijte příkazový řádek vývojáře (nebo příkazový řádek Visual Studio v systému Windows 7).</span><span class="sxs-lookup"><span data-stu-id="ec656-108">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="ec656-109">Další informace najdete v tématu [příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="ec656-109">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="ec656-110">V příkazovém řádku zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="ec656-110">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec656-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ec656-111">Syntax</span></span>  
  
```  
cert2spc cert1.cer | crl1.crl [... certN.cer | crlN.crl] outputSPCfile.spc  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ec656-112">Parametry</span><span class="sxs-lookup"><span data-stu-id="ec656-112">Parameters</span></span>  
  
|<span data-ttu-id="ec656-113">Argument</span><span class="sxs-lookup"><span data-stu-id="ec656-113">Argument</span></span>|<span data-ttu-id="ec656-114">Popis</span><span class="sxs-lookup"><span data-stu-id="ec656-114">Description</span></span>|  
|--------------|-----------------|  
|`certN.cer`|<span data-ttu-id="ec656-115">Název certifikátu X.509, který má být zahrnut do souboru SPC.</span><span class="sxs-lookup"><span data-stu-id="ec656-115">The name of an X.509 certificate to include in the SPC file.</span></span> <span data-ttu-id="ec656-116">Můžete zadat více názvů oddělených mezerami.</span><span class="sxs-lookup"><span data-stu-id="ec656-116">You can specify multiple names separated by spaces.</span></span>|  
|`crlN.crl`|<span data-ttu-id="ec656-117">Název seznamu odvolání certifikátu, který má být zahrnut do souboru SPC.</span><span class="sxs-lookup"><span data-stu-id="ec656-117">The name of a certificate revocation list to include in the SPC file.</span></span> <span data-ttu-id="ec656-118">Můžete zadat více názvů oddělených mezerami.</span><span class="sxs-lookup"><span data-stu-id="ec656-118">You can specify multiple names separated by spaces.</span></span>|  
|`outputSPCfile.spc`|<span data-ttu-id="ec656-119">Název objektu PKCS #7, který bude obsahovat certifikáty X.509.</span><span class="sxs-lookup"><span data-stu-id="ec656-119">The name of the PKCS #7 object that will contain the X.509 certificates.</span></span>|  
  
|<span data-ttu-id="ec656-120">Možnost</span><span class="sxs-lookup"><span data-stu-id="ec656-120">Option</span></span>|<span data-ttu-id="ec656-121">Popis</span><span class="sxs-lookup"><span data-stu-id="ec656-121">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="ec656-122">**/?**</span><span class="sxs-lookup"><span data-stu-id="ec656-122">**/?**</span></span>|<span data-ttu-id="ec656-123">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="ec656-123">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="ec656-124">Příklady</span><span class="sxs-lookup"><span data-stu-id="ec656-124">Examples</span></span>  
 <span data-ttu-id="ec656-125">Následující příkaz vytvoří certifikát SPC ze `myCertificate.cer` a umístí jej do `mySPCFile.spc`.</span><span class="sxs-lookup"><span data-stu-id="ec656-125">The following command creates an SPC from `myCertificate.cer` and places it in `mySPCFile.spc`.</span></span>  
  
```  
cert2spc myCertificate.cer mySPCFile.spc  
```  
  
 <span data-ttu-id="ec656-126">Následující příkaz vytvoří certifikát SPC ze `oneCertificate.cer` a `twoCertificate.cer`a umístí jej do `mySPCFile.spc`.</span><span class="sxs-lookup"><span data-stu-id="ec656-126">The following command creates an SPC from `oneCertificate.cer` and `twoCertificate.cer`, and places it in `mySPCFile.spc`.</span></span>  
  
```  
cert2spc oneCertificate.cer twoCertificate.cer mySPCFile.spc  
```  
  
## <a name="see-also"></a><span data-ttu-id="ec656-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="ec656-127">See Also</span></span>  
 [<span data-ttu-id="ec656-128">Nástroje</span><span class="sxs-lookup"><span data-stu-id="ec656-128">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="ec656-129">MakeCert.exe (nástroj pro vytvoření certifikátu)</span><span class="sxs-lookup"><span data-stu-id="ec656-129">Makecert.exe (Certificate Creation Tool)</span></span>](https://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d)  
 [<span data-ttu-id="ec656-130">Příkazové řádky</span><span class="sxs-lookup"><span data-stu-id="ec656-130">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
