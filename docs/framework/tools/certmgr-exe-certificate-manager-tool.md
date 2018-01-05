---
title: "Certmgr.exe (nástroj Certificate Manager)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates, managing
- CRLs
- certificate trust lists
- Certmgr.exe
- Certificate Manager tool
- CTLs
- certificate revocation lists
ms.assetid: 7e953b43-1374-4bbc-814f-53ca1b6b52bb
caps.latest.revision: "27"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1c303a9d91d12305bd8be4e111aaa8d6ac13eb77
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="certmgrexe-certificate-manager-tool"></a><span data-ttu-id="7b98c-102">Certmgr.exe (nástroj Certificate Manager)</span><span class="sxs-lookup"><span data-stu-id="7b98c-102">Certmgr.exe (Certificate Manager Tool)</span></span>
<span data-ttu-id="7b98c-103">Nástroj Správce certifikátů (Certmgr.exe) spravuje certifikáty, seznamy důvěryhodných certifikátů (CTL) a seznamy odvolaných certifikátů (CRL).</span><span class="sxs-lookup"><span data-stu-id="7b98c-103">The Certificate Manager tool (Certmgr.exe) manages certificates, certificate trust lists (CTLs), and certificate revocation lists (CRLs).</span></span>  
  
 <span data-ttu-id="7b98c-104">Správce certifikátů je automaticky nainstalován při instalaci sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7b98c-104">The Certificate Manager is automatically installed with Visual Studio.</span></span> <span data-ttu-id="7b98c-105">Spusťte nástroj pomocí [příkazového řádku](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="7b98c-105">To start the tool, use the [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7b98c-106">Správce certifikátů (Certmgr.exe) je nástroj příkazového řádku, zatímco Certifikáty (Certmgr.msc) jsou modulem snap-in konzoly MMC (Microsoft Management Console).</span><span class="sxs-lookup"><span data-stu-id="7b98c-106">The Certificate Manager tool (Certmgr.exe) is a command-line utility, whereas Certificates (Certmgr.msc) is a Microsoft Management Console (MMC) snap-in.</span></span> <span data-ttu-id="7b98c-107">Protože Certmgr.msc je obvykle najde v adresáři systému Windows, zadávání `certmgr` na příkazovém řádku může načíst modul snap-in Certifikáty konzoly MMC i v případě, že máte otevřený příkazový řádek sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7b98c-107">Because Certmgr.msc is usually found in the Windows System directory, entering `certmgr` at the command line may load the Certificates MMC snap-in even if you have opened the Visual Studio Command Prompt.</span></span> <span data-ttu-id="7b98c-108">K tomuto případu může dojít, protože cesta k modulu snap-in předchází cestě nástroje Správce certifikátů v proměnné prostředí PATH.</span><span class="sxs-lookup"><span data-stu-id="7b98c-108">This occurs because the path to the snap-in precedes the path to the Certificate Manager tool in the PATH environment variable.</span></span> <span data-ttu-id="7b98c-109">Setkáte-li se s tímto problémem, můžete zadáním cesty ke spustitelnému souboru spustit příkazy Certmgr.exe.</span><span class="sxs-lookup"><span data-stu-id="7b98c-109">If you encounter this problem, you can execute Certmgr.exe commands by specifying the path to the executable.</span></span>  
  
 <span data-ttu-id="7b98c-110">Tento nástroj je automaticky nainstalován se sadou Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7b98c-110">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="7b98c-111">Chcete-li spustit tento nástroj, použijte příkazový řádek vývojáře (nebo příkazový řádek Visual Studio v systému Windows 7).</span><span class="sxs-lookup"><span data-stu-id="7b98c-111">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="7b98c-112">Další informace najdete v tématu [příkazového řádku](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="7b98c-112">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="7b98c-113">Přehled certifikátů X.509 najdete v tématu [práce s certifikáty](../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="7b98c-113">For an overview of X.509 certificates, see [Working with Certificates](../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>  
  
 <span data-ttu-id="7b98c-114">V příkazovém řádku zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="7b98c-114">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b98c-115">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7b98c-115">Syntax</span></span>  
  
```  
      certmgr [/add | /del | /put] [options]  
[/s[/r registryLocation]] [sourceStorename]  
[/s[/r registryLocation]] [destinationStorename]  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7b98c-116">Parametry</span><span class="sxs-lookup"><span data-stu-id="7b98c-116">Parameters</span></span>  
  
|<span data-ttu-id="7b98c-117">Argument</span><span class="sxs-lookup"><span data-stu-id="7b98c-117">Argument</span></span>|<span data-ttu-id="7b98c-118">Popis</span><span class="sxs-lookup"><span data-stu-id="7b98c-118">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="7b98c-119">*sourceStorename*</span><span class="sxs-lookup"><span data-stu-id="7b98c-119">*sourceStorename*</span></span>|<span data-ttu-id="7b98c-120">Úložiště certifikátů obsahuje aktuální certifikáty, soubory CTL nebo CRL, které lze přidat, odstranit, uložit nebo zobrazit.</span><span class="sxs-lookup"><span data-stu-id="7b98c-120">The certificate store that contains the existing certificates, CTLs, or CRLs to add, delete, save, or display.</span></span> <span data-ttu-id="7b98c-121">To může představovat soubor úložiště nebo systémové úložiště.</span><span class="sxs-lookup"><span data-stu-id="7b98c-121">This can be a store file or a systems store.</span></span>|  
|<span data-ttu-id="7b98c-122">*destinationStorename*</span><span class="sxs-lookup"><span data-stu-id="7b98c-122">*destinationStorename*</span></span>|<span data-ttu-id="7b98c-123">Výstupní úložiště certifikátů nebo soubor.</span><span class="sxs-lookup"><span data-stu-id="7b98c-123">The output certificate store or file.</span></span>|  
  
|<span data-ttu-id="7b98c-124">Možnost</span><span class="sxs-lookup"><span data-stu-id="7b98c-124">Option</span></span>|<span data-ttu-id="7b98c-125">Popis</span><span class="sxs-lookup"><span data-stu-id="7b98c-125">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="7b98c-126">**/ add**</span><span class="sxs-lookup"><span data-stu-id="7b98c-126">**/add**</span></span>|<span data-ttu-id="7b98c-127">Přidá certifikáty, soubory CTL a CRL do úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="7b98c-127">Adds certificates, CTLs, and CRLs to a certificate store.</span></span>|  
|<span data-ttu-id="7b98c-128">**/ all**</span><span class="sxs-lookup"><span data-stu-id="7b98c-128">**/all**</span></span>|<span data-ttu-id="7b98c-129">Přidá všechny položky při použití s **/ add**.</span><span class="sxs-lookup"><span data-stu-id="7b98c-129">Adds all entries when used with **/add**.</span></span> <span data-ttu-id="7b98c-130">Umožňuje odstranit všechny položky při použití s **/del**. Zobrazí všechny položky při použití bez **/ add** nebo **/del** možnosti.</span><span class="sxs-lookup"><span data-stu-id="7b98c-130">Deletes all entries when used with **/del**. Displays all entries when used without the **/add** or **/del** options.</span></span> <span data-ttu-id="7b98c-131">**Nebo všechny** možnost nelze použít s **/put**.</span><span class="sxs-lookup"><span data-stu-id="7b98c-131">The **/all** option cannot be used with **/put**.</span></span>|  
|<span data-ttu-id="7b98c-132">**/c**</span><span class="sxs-lookup"><span data-stu-id="7b98c-132">**/c**</span></span>|<span data-ttu-id="7b98c-133">Přidá certifikáty při použití s **/ add**.</span><span class="sxs-lookup"><span data-stu-id="7b98c-133">Adds certificates when used with **/add**.</span></span> <span data-ttu-id="7b98c-134">Odstraní certifikáty při použití s **/del**. Uloží certifikáty při použití s **/put**.</span><span class="sxs-lookup"><span data-stu-id="7b98c-134">Deletes certificates when used with **/del**. Saves certificates when used with **/put**.</span></span> <span data-ttu-id="7b98c-135">Zobrazí certifikáty při použití bez **/ add**, **/del**, nebo **/put** možnost.</span><span class="sxs-lookup"><span data-stu-id="7b98c-135">Displays certificates when used without the **/add**, **/del**, or **/put** option.</span></span>|  
|<span data-ttu-id="7b98c-136">**NEBO SEZNAMU ODVOLANÝCH CERTIFIKÁTŮ**</span><span class="sxs-lookup"><span data-stu-id="7b98c-136">**/CRL**</span></span>|<span data-ttu-id="7b98c-137">Přidá seznamy CRL při použití s **/ add**.</span><span class="sxs-lookup"><span data-stu-id="7b98c-137">Adds CRLs when used with **/add**.</span></span> <span data-ttu-id="7b98c-138">Odstraní seznamy CRL při použití s **/del**. Uloží seznamy CRL při použití s **/put**.</span><span class="sxs-lookup"><span data-stu-id="7b98c-138">Deletes CRLs when used with **/del**. Saves CRLs when used with **/put**.</span></span> <span data-ttu-id="7b98c-139">Zobrazí seznamy CRL při použití bez **/ add**, **/del**, nebo **/put** možnost.</span><span class="sxs-lookup"><span data-stu-id="7b98c-139">Displays CRLs when used without the **/add**, **/del**, or **/put** option.</span></span>|  
|<span data-ttu-id="7b98c-140">**/ CTL**</span><span class="sxs-lookup"><span data-stu-id="7b98c-140">**/CTL**</span></span>|<span data-ttu-id="7b98c-141">Přidá seznamy CTL při použití s **/ add**.</span><span class="sxs-lookup"><span data-stu-id="7b98c-141">Adds CTLs when used with **/add**.</span></span> <span data-ttu-id="7b98c-142">Odstraní seznamy CTL při použití s **/del**. Uloží seznamy CTL při použití s **/put**.</span><span class="sxs-lookup"><span data-stu-id="7b98c-142">Deletes CTLs when used with **/del**. Saves CTLs when used with **/put**.</span></span> <span data-ttu-id="7b98c-143">Zobrazí seznamy CTL při použití bez **/ add**, **/del**, nebo **/put** možnost.</span><span class="sxs-lookup"><span data-stu-id="7b98c-143">Displays CTLs when used without the **/add**, **/del**, or **/put** option.</span></span>|  
|<span data-ttu-id="7b98c-144">**/ del**</span><span class="sxs-lookup"><span data-stu-id="7b98c-144">**/del**</span></span>|<span data-ttu-id="7b98c-145">Odstraní certifikáty, soubory CTL a CRL z úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="7b98c-145">Deletes certificates, CTLs, and CRLs from a certificate store.</span></span>|  
|<span data-ttu-id="7b98c-146">**/e** *encodingType*</span><span class="sxs-lookup"><span data-stu-id="7b98c-146">**/e** *encodingType*</span></span>|<span data-ttu-id="7b98c-147">Určuje typ kódování certifikátu.</span><span class="sxs-lookup"><span data-stu-id="7b98c-147">Specifies the certificate encoding type.</span></span> <span data-ttu-id="7b98c-148">Výchozí hodnota je `X509_ASN_ENCODING`.</span><span class="sxs-lookup"><span data-stu-id="7b98c-148">The default is `X509_ASN_ENCODING`.</span></span>|  
|<span data-ttu-id="7b98c-149">**/f** *dwFlags*</span><span class="sxs-lookup"><span data-stu-id="7b98c-149">**/f** *dwFlags*</span></span>|<span data-ttu-id="7b98c-150">Určuje příznak pro otevření úložiště.</span><span class="sxs-lookup"><span data-stu-id="7b98c-150">Specifies the store open flag.</span></span> <span data-ttu-id="7b98c-151">Toto je *dwFlags* byl předán parametr **příkaz CertOpenStore**.</span><span class="sxs-lookup"><span data-stu-id="7b98c-151">This is the *dwFlags* parameter passed to **CertOpenStore**.</span></span> <span data-ttu-id="7b98c-152">Výchozí hodnota je CERT_SYSTEM_STORE_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="7b98c-152">The default value is CERT_SYSTEM_STORE_CURRENT_USER.</span></span> <span data-ttu-id="7b98c-153">Tato možnost je považován za pouze, pokud **/y** možnost se používá.</span><span class="sxs-lookup"><span data-stu-id="7b98c-153">This option is considered only if the **/y** option is used.</span></span>|  
|<span data-ttu-id="7b98c-154">**/h**[**nápovědu**]</span><span class="sxs-lookup"><span data-stu-id="7b98c-154">**/h**[**elp**]</span></span>|<span data-ttu-id="7b98c-155">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="7b98c-155">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="7b98c-156">**/n***osoby*</span><span class="sxs-lookup"><span data-stu-id="7b98c-156">**/n** *nam*</span></span>|<span data-ttu-id="7b98c-157">Určuje obecný název certifikátu, který se má přidat, odstranit nebo uložit.</span><span class="sxs-lookup"><span data-stu-id="7b98c-157">Specifies the common name of the certificate to add, delete, or save.</span></span> <span data-ttu-id="7b98c-158">Tuto možnost lze použít u certifikátů. Nelze ji použít u souborů CTL nebo u CRL.</span><span class="sxs-lookup"><span data-stu-id="7b98c-158">This option can only be used with certificates; it cannot be used with CTLs or CRLs.</span></span>|  
|<span data-ttu-id="7b98c-159">**/ Vložení**</span><span class="sxs-lookup"><span data-stu-id="7b98c-159">**/put**</span></span>|<span data-ttu-id="7b98c-160">Uloží do souboru certifikát X.509, soubor CTL nebo CRL z úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="7b98c-160">Saves an X.509 certificate, CTL, or CRL from a certificate store to a file.</span></span> <span data-ttu-id="7b98c-161">Soubor je uložen ve formátu X.509.</span><span class="sxs-lookup"><span data-stu-id="7b98c-161">The file is saved in X.509 format.</span></span> <span data-ttu-id="7b98c-162">Můžete použít **/7** možnost s **/put** možnost uložení souboru ve formátu PKCS #7.</span><span class="sxs-lookup"><span data-stu-id="7b98c-162">You can use the **/7** option with the **/put** option to save the file in PKCS #7 format.</span></span> <span data-ttu-id="7b98c-163">**/Put** možnost musí být následováno buď **/c**, **/CTL**, nebo **/CRL**.</span><span class="sxs-lookup"><span data-stu-id="7b98c-163">The **/put** option must be followed by either **/c**, **/CTL**, or **/CRL**.</span></span> <span data-ttu-id="7b98c-164">**Nebo všechny** možnost nelze použít s **/put**.</span><span class="sxs-lookup"><span data-stu-id="7b98c-164">The **/all** option cannot be used with **/put**.</span></span>|  
|<span data-ttu-id="7b98c-165">**/r** *umístění*</span><span class="sxs-lookup"><span data-stu-id="7b98c-165">**/r** *location*</span></span>|<span data-ttu-id="7b98c-166">Určuje umístění registru v rámci systémového úložiště.</span><span class="sxs-lookup"><span data-stu-id="7b98c-166">Identifies the registry location of the system store.</span></span> <span data-ttu-id="7b98c-167">Tato možnost je považován za pouze v případě, že zadáte **/s** možnost.</span><span class="sxs-lookup"><span data-stu-id="7b98c-167">This option is considered only if you specify the **/s** option.</span></span> <span data-ttu-id="7b98c-168">*umístění* musí mít jednu z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="7b98c-168">*location* must be one of the following:</span></span><br /><br /> <span data-ttu-id="7b98c-169">-   `currentUser`Označuje, že úložiště certifikátů je pod klíčem HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="7b98c-169">-   `currentUser` indicates that the certificate store is under the HKEY_CURRENT_USER key.</span></span> <span data-ttu-id="7b98c-170">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="7b98c-170">This is the default.</span></span><br /><span data-ttu-id="7b98c-171">-   `localMachine`Označuje, že úložiště certifikátů je pod klíčem HKEY_LOCAL_MACHINE.</span><span class="sxs-lookup"><span data-stu-id="7b98c-171">-   `localMachine` indicates that the certificate store is under the HKEY_LOCAL_MACHINE key.</span></span>|  
|<span data-ttu-id="7b98c-172">**/s**</span><span class="sxs-lookup"><span data-stu-id="7b98c-172">**/s**</span></span>|<span data-ttu-id="7b98c-173">Určuje, že je úložiště certifikátů systémovým úložištěm.</span><span class="sxs-lookup"><span data-stu-id="7b98c-173">Indicates that the certificate store is a system store.</span></span> <span data-ttu-id="7b98c-174">Pokud nezadáte tuto možnost, se považuje za úložiště **StoreFile**.</span><span class="sxs-lookup"><span data-stu-id="7b98c-174">If you do not specify this option, the store is considered to be a **StoreFile**.</span></span>|  
|<span data-ttu-id="7b98c-175">**/SHA1** *sha1Hash*</span><span class="sxs-lookup"><span data-stu-id="7b98c-175">**/sha1** *sha1Hash*</span></span>|<span data-ttu-id="7b98c-176">Určuje hodnotu hash SHA1 certifikátu, souboru CTl nebo CRl, který se má přidat, odstranit nebo uložit.</span><span class="sxs-lookup"><span data-stu-id="7b98c-176">Specifies the SHA1 hash of the certificate, CTL, or CRL to add, delete, or save.</span></span>|  
|<span data-ttu-id="7b98c-177">**/v**</span><span class="sxs-lookup"><span data-stu-id="7b98c-177">**/v**</span></span>|<span data-ttu-id="7b98c-178">Určuje podrobný režim. Zobrazí detailní informace o certifikátech, souborech CTL a CRL.</span><span class="sxs-lookup"><span data-stu-id="7b98c-178">Specifies verbose mode; displays detailed information about certificates, CTLs, and CRLs.</span></span> <span data-ttu-id="7b98c-179">Tuto možnost nelze použít s **/ add**, **/del**, nebo **/put** možnosti.</span><span class="sxs-lookup"><span data-stu-id="7b98c-179">This option cannot be used with the **/add**, **/del**, or **/put** options.</span></span>|  
|<span data-ttu-id="7b98c-180">**/y** *zprostředkovatele*</span><span class="sxs-lookup"><span data-stu-id="7b98c-180">**/y** *provider*</span></span>|<span data-ttu-id="7b98c-181">Určuje název poskytovatele úložiště.</span><span class="sxs-lookup"><span data-stu-id="7b98c-181">Specifies the store provider name.</span></span>|  
|<span data-ttu-id="7b98c-182">**/7**</span><span class="sxs-lookup"><span data-stu-id="7b98c-182">**/7**</span></span>|<span data-ttu-id="7b98c-183">Ukládá cílové úložiště jako objekt PKCS #7.</span><span class="sxs-lookup"><span data-stu-id="7b98c-183">Saves the destination store as a PKCS #7 object.</span></span>|  
|<span data-ttu-id="7b98c-184">**/?**</span><span class="sxs-lookup"><span data-stu-id="7b98c-184">**/?**</span></span>|<span data-ttu-id="7b98c-185">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="7b98c-185">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b98c-186">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7b98c-186">Remarks</span></span>  
 <span data-ttu-id="7b98c-187">Nástroj Certmgr.exe vykonává následující základní funkce:</span><span class="sxs-lookup"><span data-stu-id="7b98c-187">Certmgr.exe performs the following basic functions:</span></span>  
  
-   <span data-ttu-id="7b98c-188">Zobrazí certifikáty, soubory CTL a CRL do konzoly.</span><span class="sxs-lookup"><span data-stu-id="7b98c-188">Displays certificates, CTLs, and CRLs to the console.</span></span>  
  
-   <span data-ttu-id="7b98c-189">Přidá certifikáty, soubory CTL a CRL do úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="7b98c-189">Adds certificates, CTLs, and CRLs to a certificate store.</span></span>  
  
-   <span data-ttu-id="7b98c-190">Odstraní certifikáty, soubory CTL a CRL z úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="7b98c-190">Deletes certificates, CTLs, and CRLs from a certificate store.</span></span>  
  
-   <span data-ttu-id="7b98c-191">Uloží do souboru certifikát X.509, soubor CTL nebo CRL z úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="7b98c-191">Saves an X.509 certificate, CTL, or CRL from a certificate store to a file.</span></span>  
  
 <span data-ttu-id="7b98c-192">Certmgr.exe funguje s dva typy úložišť certifikátů: **StoreFile** a úložiště systému.</span><span class="sxs-lookup"><span data-stu-id="7b98c-192">Certmgr.exe works with two types of certificate stores: **StoreFile** and system store.</span></span> <span data-ttu-id="7b98c-193">Není nutné zadávat typ úložiště certifikátů. Certmgr.exe dokáže rozpoznat typ úložiště a vykonat příslušné operace.</span><span class="sxs-lookup"><span data-stu-id="7b98c-193">It is not necessary to specify the type of certificate store; Certmgr.exe can identify the store type and perform the appropriate operations.</span></span>  
  
 <span data-ttu-id="7b98c-194">Spuštěním nástroje Certmgr.exe bez určení jakýchkoli možností dojde ke spuštění modulu snap-in certmgr.msc, který obsahuje uživatelské rozhraní, které pomáhá s úlohami správy certifikátů, které jsou dostupné také z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="7b98c-194">Running Certmgr.exe without specifying any options launches the certmgr.msc snap-in, which has a GUI that helps with the certificate management tasks that are also available from the command line.</span></span> <span data-ttu-id="7b98c-195">Uživatelské rozhraní poskytuje průvodce importováním, který zkopíruje certifikáty, soubory CTL a CRL z disku do úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="7b98c-195">The GUI provides an import wizard, which copies certificates, CTLs, and CRLs from your disk to a certificate store.</span></span>  
  
 <span data-ttu-id="7b98c-196">Názvy úložiště certifikátu x 509 pro můžete najít `sourceStorename` a `destinationStorename` parametry kompilování a spuštěním následující kód.</span><span class="sxs-lookup"><span data-stu-id="7b98c-196">You can find the names of X509Certificate stores for the `sourceStorename` and `destinationStorename` parameters by compiling and running the following code.</span></span>  
  
 [!code-csharp[Tools.CertMgr#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tools.certmgr/cs/storenames1.cs#1)]
 [!code-vb[Tools.CertMgr#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tools.certmgr/vb/storenames1.vb#1)]  
  
 <span data-ttu-id="7b98c-197">Další informace o certifikátech najdete v tématu [práce s certifikáty](../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="7b98c-197">For more information about certificates, see [Working with Certificates](../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="7b98c-198">Příklady</span><span class="sxs-lookup"><span data-stu-id="7b98c-198">Examples</span></span>  
 <span data-ttu-id="7b98c-199">Následující příkaz zobrazí výchozí úložiště systému, který volá `my` s podrobným výstupem.</span><span class="sxs-lookup"><span data-stu-id="7b98c-199">The following command displays a default system store called `my` with verbose output.</span></span>  
  
```  
certmgr /v /s my  
```  
  
 <span data-ttu-id="7b98c-200">Následující příkaz přidá všechny certifikáty v souboru s názvem `myFile.ext` nový soubor s názvem `newFile.ext`.</span><span class="sxs-lookup"><span data-stu-id="7b98c-200">The following command adds all the certificates in a file called `myFile.ext` to a new file called `newFile.ext`.</span></span>  
  
```  
certmgr /add /all /c myFile.ext newFile.ext  
```  
  
 <span data-ttu-id="7b98c-201">Následující příkaz přidá certifikát do souboru s názvem `testcert.cer` k `my` úložiště systému.</span><span class="sxs-lookup"><span data-stu-id="7b98c-201">The following command adds the certificate in a file named `testcert.cer` to the `my` system store.</span></span>  
  
```  
certmgr /add /c testcert.cer /s my  
```  
  
 <span data-ttu-id="7b98c-202">Následující příkaz přidá certifikát do souboru s názvem `TrustedCert.cer` do kořenového úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="7b98c-202">The following command adds the certificate in a file named `TrustedCert.cer` to the root certificate store.</span></span>  
  
```  
certmgr /c /add TrustedCert.cer /s root  
```  
  
 <span data-ttu-id="7b98c-203">Následující příkaz uloží certifikát s běžným názvem `myCert` v `my` volá úložiště systému do souboru `newCert.cer`.</span><span class="sxs-lookup"><span data-stu-id="7b98c-203">The following command saves a certificate with the common name `myCert` in the `my` system store to a file called `newCert.cer`.</span></span>  
  
```  
certmgr /add /c /n myCert /s my newCert.cer  
```  
  
 <span data-ttu-id="7b98c-204">Následující příkaz odstraní všechny seznamy CTL v `my` úložiště systému a uloží výsledné úložiště do souboru názvem `newStore.str`.</span><span class="sxs-lookup"><span data-stu-id="7b98c-204">The following command deletes all CTLs in the `my` system store and saves the resulting store to a file called `newStore.str`.</span></span>  
  
```  
certmgr /del /all /ctl /s my newStore.str  
```  
  
 <span data-ttu-id="7b98c-205">Následující příkaz uloží v certifikát `my` úložiště systému v souboru `newFile`.</span><span class="sxs-lookup"><span data-stu-id="7b98c-205">The following command saves a certificate in the `my` system store in the file `newFile`.</span></span> <span data-ttu-id="7b98c-206">Zobrazí se výzva k zadání číslo certifikátu z `my` uvést do `newFile`.</span><span class="sxs-lookup"><span data-stu-id="7b98c-206">You will be prompted to enter the certificate number from `my` to put in `newFile`.</span></span>  
  
```  
certmgr /put /c /s my newFile  
```  
  
## <a name="see-also"></a><span data-ttu-id="7b98c-207">Viz také</span><span class="sxs-lookup"><span data-stu-id="7b98c-207">See Also</span></span>  
 [<span data-ttu-id="7b98c-208">Nástroje</span><span class="sxs-lookup"><span data-stu-id="7b98c-208">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="7b98c-209">MakeCert.exe (nástroj pro vytvoření certifikátu)</span><span class="sxs-lookup"><span data-stu-id="7b98c-209">Makecert.exe (Certificate Creation Tool)</span></span>](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d)  
 [<span data-ttu-id="7b98c-210">Příkazové řádky</span><span class="sxs-lookup"><span data-stu-id="7b98c-210">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
