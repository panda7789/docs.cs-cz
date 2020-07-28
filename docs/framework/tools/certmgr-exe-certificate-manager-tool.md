---
title: Certmgr.exe (nástroj Certificate Manager)
description: Prozkoumejte Certmgr.exe nástroje Správce certifikátů. Tento nástroj spravuje certifikáty, seznamy důvěryhodných certifikátů (CTL) a seznamy odvolaných certifikátů (CRL).
ms.date: 03/30/2017
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
ms.openlocfilehash: 43ab281e6ec28ff23ea584b03fd4278c6682e33e
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167259"
---
# <a name="certmgrexe-certificate-manager-tool"></a><span data-ttu-id="773dc-104">Certmgr.exe (nástroj Certificate Manager)</span><span class="sxs-lookup"><span data-stu-id="773dc-104">Certmgr.exe (Certificate Manager Tool)</span></span>
<span data-ttu-id="773dc-105">Nástroj Správce certifikátů (Certmgr.exe) spravuje certifikáty, seznamy důvěryhodných certifikátů (CTL) a seznamy odvolaných certifikátů (CRL).</span><span class="sxs-lookup"><span data-stu-id="773dc-105">The Certificate Manager tool (Certmgr.exe) manages certificates, certificate trust lists (CTLs), and certificate revocation lists (CRLs).</span></span>  
  
 <span data-ttu-id="773dc-106">Správce certifikátů je automaticky nainstalován při instalaci sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="773dc-106">The Certificate Manager is automatically installed with Visual Studio.</span></span> <span data-ttu-id="773dc-107">Chcete-li spustit nástroj, použijte [příkaz s výzvou](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="773dc-107">To start the tool, use the [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="773dc-108">Správce certifikátů (Certmgr.exe) je nástroj příkazového řádku, zatímco Certifikáty (Certmgr.msc) jsou modulem snap-in konzoly MMC (Microsoft Management Console).</span><span class="sxs-lookup"><span data-stu-id="773dc-108">The Certificate Manager tool (Certmgr.exe) is a command-line utility, whereas Certificates (Certmgr.msc) is a Microsoft Management Console (MMC) snap-in.</span></span> <span data-ttu-id="773dc-109">Vzhledem k tomu, že certmgr. msc se obvykle nachází v systémovém adresáři Windows, může se při zadávání do `certmgr` příkazového řádku načíst modul snap-in Certifikáty konzoly MMC i v případě, že jste otevřeli Developer Command Prompt pro Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="773dc-109">Because Certmgr.msc is usually found in the Windows System directory, entering `certmgr` at the command line may load the Certificates MMC snap-in even if you have opened the Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="773dc-110">K tomuto případu může dojít, protože cesta k modulu snap-in předchází cestě nástroje Správce certifikátů v proměnné prostředí PATH.</span><span class="sxs-lookup"><span data-stu-id="773dc-110">This occurs because the path to the snap-in precedes the path to the Certificate Manager tool in the PATH environment variable.</span></span> <span data-ttu-id="773dc-111">Setkáte-li se s tímto problémem, můžete zadáním cesty ke spustitelnému souboru spustit příkazy Certmgr.exe.</span><span class="sxs-lookup"><span data-stu-id="773dc-111">If you encounter this problem, you can execute Certmgr.exe commands by specifying the path to the executable.</span></span>  
  
 <span data-ttu-id="773dc-112">Tento nástroj je automaticky nainstalován se sadou Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="773dc-112">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="773dc-113">Chcete-li spustit nástroj, použijte Developer Command Prompt pro Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7).</span><span class="sxs-lookup"><span data-stu-id="773dc-113">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="773dc-114">Další informace najdete v tématu [výzvy k zadání příkazu](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="773dc-114">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="773dc-115">Přehled certifikátů X. 509 najdete v tématu [práce s certifikáty](../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="773dc-115">For an overview of X.509 certificates, see [Working with Certificates](../wcf/feature-details/working-with-certificates.md).</span></span>  
  
 <span data-ttu-id="773dc-116">V příkazovém řádku zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="773dc-116">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="773dc-117">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="773dc-117">Syntax</span></span>  
  
```console  
      certmgr [/add | /del | /put] [options]  
[/s[/r registryLocation]] [sourceStorename]  
[/s[/r registryLocation]] [destinationStorename]  
```  
  
## <a name="parameters"></a><span data-ttu-id="773dc-118">Parametry</span><span class="sxs-lookup"><span data-stu-id="773dc-118">Parameters</span></span>  
  
|<span data-ttu-id="773dc-119">Argument</span><span class="sxs-lookup"><span data-stu-id="773dc-119">Argument</span></span>|<span data-ttu-id="773dc-120">Popis</span><span class="sxs-lookup"><span data-stu-id="773dc-120">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="773dc-121">*Certifikátů*</span><span class="sxs-lookup"><span data-stu-id="773dc-121">*sourceStorename*</span></span>|<span data-ttu-id="773dc-122">Úložiště certifikátů obsahuje aktuální certifikáty, soubory CTL nebo CRL, které lze přidat, odstranit, uložit nebo zobrazit.</span><span class="sxs-lookup"><span data-stu-id="773dc-122">The certificate store that contains the existing certificates, CTLs, or CRLs to add, delete, save, or display.</span></span> <span data-ttu-id="773dc-123">To může představovat soubor úložiště nebo systémové úložiště.</span><span class="sxs-lookup"><span data-stu-id="773dc-123">This can be a store file or a systems store.</span></span>|  
|<span data-ttu-id="773dc-124">*destinationStorename*</span><span class="sxs-lookup"><span data-stu-id="773dc-124">*destinationStorename*</span></span>|<span data-ttu-id="773dc-125">Výstupní úložiště certifikátů nebo soubor.</span><span class="sxs-lookup"><span data-stu-id="773dc-125">The output certificate store or file.</span></span>|  
  
|<span data-ttu-id="773dc-126">Možnost</span><span class="sxs-lookup"><span data-stu-id="773dc-126">Option</span></span>|<span data-ttu-id="773dc-127">Popis</span><span class="sxs-lookup"><span data-stu-id="773dc-127">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="773dc-128">**/Add**</span><span class="sxs-lookup"><span data-stu-id="773dc-128">**/add**</span></span>|<span data-ttu-id="773dc-129">Přidá certifikáty, soubory CTL a CRL do úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="773dc-129">Adds certificates, CTLs, and CRLs to a certificate store.</span></span>|  
|<span data-ttu-id="773dc-130">**/All**</span><span class="sxs-lookup"><span data-stu-id="773dc-130">**/all**</span></span>|<span data-ttu-id="773dc-131">Přidá všechny položky při použití s **/Add**.</span><span class="sxs-lookup"><span data-stu-id="773dc-131">Adds all entries when used with **/add**.</span></span> <span data-ttu-id="773dc-132">Odstraní všechny položky při použití s **/del**. Zobrazí všechny položky, pokud jsou použity bez možností **/Add** nebo **/del** .</span><span class="sxs-lookup"><span data-stu-id="773dc-132">Deletes all entries when used with **/del**. Displays all entries when used without the **/add** or **/del** options.</span></span> <span data-ttu-id="773dc-133">Možnost **/All** nelze použít s **/Put**.</span><span class="sxs-lookup"><span data-stu-id="773dc-133">The **/all** option cannot be used with **/put**.</span></span>|  
|<span data-ttu-id="773dc-134">**/c**</span><span class="sxs-lookup"><span data-stu-id="773dc-134">**/c**</span></span>|<span data-ttu-id="773dc-135">Přidá certifikáty při použití s **/Add**.</span><span class="sxs-lookup"><span data-stu-id="773dc-135">Adds certificates when used with **/add**.</span></span> <span data-ttu-id="773dc-136">Odstraní certifikáty při použití s **/del**. Ukládá certifikáty při použití s **/Put**.</span><span class="sxs-lookup"><span data-stu-id="773dc-136">Deletes certificates when used with **/del**. Saves certificates when used with **/put**.</span></span> <span data-ttu-id="773dc-137">Zobrazí certifikáty při použití bez možnosti **/Add**, **/del**nebo **/Put** .</span><span class="sxs-lookup"><span data-stu-id="773dc-137">Displays certificates when used without the **/add**, **/del**, or **/put** option.</span></span>|  
|<span data-ttu-id="773dc-138">**/CRL**</span><span class="sxs-lookup"><span data-stu-id="773dc-138">**/CRL**</span></span>|<span data-ttu-id="773dc-139">Přidá seznam CRL při použití s **/Add**.</span><span class="sxs-lookup"><span data-stu-id="773dc-139">Adds CRLs when used with **/add**.</span></span> <span data-ttu-id="773dc-140">Odstraní seznamy odvolaných certifikátů při použití s **/del**. Při použití s **/Put**ukládá seznamy CRL.</span><span class="sxs-lookup"><span data-stu-id="773dc-140">Deletes CRLs when used with **/del**. Saves CRLs when used with **/put**.</span></span> <span data-ttu-id="773dc-141">Zobrazí seznam CRL při použití bez možnosti **/Add**, **/del**nebo **/Put** .</span><span class="sxs-lookup"><span data-stu-id="773dc-141">Displays CRLs when used without the **/add**, **/del**, or **/put** option.</span></span>|  
|<span data-ttu-id="773dc-142">**/CTL**</span><span class="sxs-lookup"><span data-stu-id="773dc-142">**/CTL**</span></span>|<span data-ttu-id="773dc-143">Přidá seznamy CTL při použití s **/Add**.</span><span class="sxs-lookup"><span data-stu-id="773dc-143">Adds CTLs when used with **/add**.</span></span> <span data-ttu-id="773dc-144">Odstraní seznamy CTL při použití s **/del**. Při použití s **/Put**ukládá seznamy CTL.</span><span class="sxs-lookup"><span data-stu-id="773dc-144">Deletes CTLs when used with **/del**. Saves CTLs when used with **/put**.</span></span> <span data-ttu-id="773dc-145">Zobrazí seznam CTL při použití bez možnosti **/Add**, **/del**nebo **/Put** .</span><span class="sxs-lookup"><span data-stu-id="773dc-145">Displays CTLs when used without the **/add**, **/del**, or **/put** option.</span></span>|  
|<span data-ttu-id="773dc-146">**/del**</span><span class="sxs-lookup"><span data-stu-id="773dc-146">**/del**</span></span>|<span data-ttu-id="773dc-147">Odstraní certifikáty, soubory CTL a CRL z úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="773dc-147">Deletes certificates, CTLs, and CRLs from a certificate store.</span></span>|  
|<span data-ttu-id="773dc-148">**/E** *EncodingType*</span><span class="sxs-lookup"><span data-stu-id="773dc-148">**/e** *encodingType*</span></span>|<span data-ttu-id="773dc-149">Určuje typ kódování certifikátu.</span><span class="sxs-lookup"><span data-stu-id="773dc-149">Specifies the certificate encoding type.</span></span> <span data-ttu-id="773dc-150">Výchozí formát je `X509_ASN_ENCODING`.</span><span class="sxs-lookup"><span data-stu-id="773dc-150">The default is `X509_ASN_ENCODING`.</span></span>|  
|<span data-ttu-id="773dc-151">**/F** *dwFlags*</span><span class="sxs-lookup"><span data-stu-id="773dc-151">**/f** *dwFlags*</span></span>|<span data-ttu-id="773dc-152">Určuje příznak pro otevření úložiště.</span><span class="sxs-lookup"><span data-stu-id="773dc-152">Specifies the store open flag.</span></span> <span data-ttu-id="773dc-153">Toto je parametr *dwFlags* předaný do **CertOpenStore**.</span><span class="sxs-lookup"><span data-stu-id="773dc-153">This is the *dwFlags* parameter passed to **CertOpenStore**.</span></span> <span data-ttu-id="773dc-154">Výchozí hodnota je CERT_SYSTEM_STORE_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="773dc-154">The default value is CERT_SYSTEM_STORE_CURRENT_USER.</span></span> <span data-ttu-id="773dc-155">Tato možnost je zvážena pouze v případě, že je použita možnost **/y** .</span><span class="sxs-lookup"><span data-stu-id="773dc-155">This option is considered only if the **/y** option is used.</span></span>|  
|<span data-ttu-id="773dc-156">**/h**[**ELP**]</span><span class="sxs-lookup"><span data-stu-id="773dc-156">**/h**[**elp**]</span></span>|<span data-ttu-id="773dc-157">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="773dc-157">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="773dc-158">**/n** *nam*</span><span class="sxs-lookup"><span data-stu-id="773dc-158">**/n** *nam*</span></span>|<span data-ttu-id="773dc-159">Určuje obecný název certifikátu, který se má přidat, odstranit nebo uložit.</span><span class="sxs-lookup"><span data-stu-id="773dc-159">Specifies the common name of the certificate to add, delete, or save.</span></span> <span data-ttu-id="773dc-160">Tuto možnost lze použít u certifikátů. Nelze ji použít u souborů CTL nebo u CRL.</span><span class="sxs-lookup"><span data-stu-id="773dc-160">This option can only be used with certificates; it cannot be used with CTLs or CRLs.</span></span>|  
|<span data-ttu-id="773dc-161">**/Put**</span><span class="sxs-lookup"><span data-stu-id="773dc-161">**/put**</span></span>|<span data-ttu-id="773dc-162">Uloží do souboru certifikát X.509, soubor CTL nebo CRL z úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="773dc-162">Saves an X.509 certificate, CTL, or CRL from a certificate store to a file.</span></span> <span data-ttu-id="773dc-163">Soubor je uložen ve formátu X.509.</span><span class="sxs-lookup"><span data-stu-id="773dc-163">The file is saved in X.509 format.</span></span> <span data-ttu-id="773dc-164">K uložení souboru ve formátu PKCS #7 můžete použít možnost **/7** s možností **/Put** .</span><span class="sxs-lookup"><span data-stu-id="773dc-164">You can use the **/7** option with the **/put** option to save the file in PKCS #7 format.</span></span> <span data-ttu-id="773dc-165">Pro možnost **/Put** musí následovat buď **/c**, **/CTL**nebo **/CRL**.</span><span class="sxs-lookup"><span data-stu-id="773dc-165">The **/put** option must be followed by either **/c**, **/CTL**, or **/CRL**.</span></span> <span data-ttu-id="773dc-166">Možnost **/All** nelze použít s **/Put**.</span><span class="sxs-lookup"><span data-stu-id="773dc-166">The **/all** option cannot be used with **/put**.</span></span>|  
|<span data-ttu-id="773dc-167">**/r** *umístění*</span><span class="sxs-lookup"><span data-stu-id="773dc-167">**/r** *location*</span></span>|<span data-ttu-id="773dc-168">Určuje umístění registru v rámci systémového úložiště.</span><span class="sxs-lookup"><span data-stu-id="773dc-168">Identifies the registry location of the system store.</span></span> <span data-ttu-id="773dc-169">Tato možnost je zvážena pouze v případě, že zadáte možnost **/s** .</span><span class="sxs-lookup"><span data-stu-id="773dc-169">This option is considered only if you specify the **/s** option.</span></span> <span data-ttu-id="773dc-170">*umístění* musí být jedna z následujících:</span><span class="sxs-lookup"><span data-stu-id="773dc-170">*location* must be one of the following:</span></span><br /><br /> <span data-ttu-id="773dc-171">-   `currentUser`označuje, že úložiště certifikátů je pod klíčem HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="773dc-171">-   `currentUser` indicates that the certificate store is under the HKEY_CURRENT_USER key.</span></span> <span data-ttu-id="773dc-172">Tato možnost je výchozí.</span><span class="sxs-lookup"><span data-stu-id="773dc-172">This is the default.</span></span><br /><span data-ttu-id="773dc-173">-   `localMachine`označuje, že úložiště certifikátů je pod klíčem HKEY_LOCAL_MACHINE.</span><span class="sxs-lookup"><span data-stu-id="773dc-173">-   `localMachine` indicates that the certificate store is under the HKEY_LOCAL_MACHINE key.</span></span>|  
|<span data-ttu-id="773dc-174">**parametr**</span><span class="sxs-lookup"><span data-stu-id="773dc-174">**/s**</span></span>|<span data-ttu-id="773dc-175">Určuje, že je úložiště certifikátů systémovým úložištěm.</span><span class="sxs-lookup"><span data-stu-id="773dc-175">Indicates that the certificate store is a system store.</span></span> <span data-ttu-id="773dc-176">Pokud tuto možnost nezadáte, považuje se za úložiště za **StoreFile**.</span><span class="sxs-lookup"><span data-stu-id="773dc-176">If you do not specify this option, the store is considered to be a **StoreFile**.</span></span>|  
|<span data-ttu-id="773dc-177">**/SHA1** *sha1Hash*</span><span class="sxs-lookup"><span data-stu-id="773dc-177">**/sha1** *sha1Hash*</span></span>|<span data-ttu-id="773dc-178">Určuje hodnotu hash SHA1 certifikátu, souboru CTl nebo CRl, který se má přidat, odstranit nebo uložit.</span><span class="sxs-lookup"><span data-stu-id="773dc-178">Specifies the SHA1 hash of the certificate, CTL, or CRL to add, delete, or save.</span></span>|  
|<span data-ttu-id="773dc-179">**/v**</span><span class="sxs-lookup"><span data-stu-id="773dc-179">**/v**</span></span>|<span data-ttu-id="773dc-180">Určuje podrobný režim. Zobrazí detailní informace o certifikátech, souborech CTL a CRL.</span><span class="sxs-lookup"><span data-stu-id="773dc-180">Specifies verbose mode; displays detailed information about certificates, CTLs, and CRLs.</span></span> <span data-ttu-id="773dc-181">Tuto možnost nelze použít s možnostmi **/Add**, **/del**nebo **/Put** .</span><span class="sxs-lookup"><span data-stu-id="773dc-181">This option cannot be used with the **/add**, **/del**, or **/put** options.</span></span>|  
|<span data-ttu-id="773dc-182">**/y** – *poskytovatel*</span><span class="sxs-lookup"><span data-stu-id="773dc-182">**/y** *provider*</span></span>|<span data-ttu-id="773dc-183">Určuje název poskytovatele úložiště.</span><span class="sxs-lookup"><span data-stu-id="773dc-183">Specifies the store provider name.</span></span>|  
|<span data-ttu-id="773dc-184">**/7**</span><span class="sxs-lookup"><span data-stu-id="773dc-184">**/7**</span></span>|<span data-ttu-id="773dc-185">Ukládá cílové úložiště jako objekt PKCS #7.</span><span class="sxs-lookup"><span data-stu-id="773dc-185">Saves the destination store as a PKCS #7 object.</span></span>|  
|<span data-ttu-id="773dc-186">**/?**</span><span class="sxs-lookup"><span data-stu-id="773dc-186">**/?**</span></span>|<span data-ttu-id="773dc-187">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="773dc-187">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="773dc-188">Poznámky</span><span class="sxs-lookup"><span data-stu-id="773dc-188">Remarks</span></span>  
 <span data-ttu-id="773dc-189">Nástroj Certmgr.exe vykonává následující základní funkce:</span><span class="sxs-lookup"><span data-stu-id="773dc-189">Certmgr.exe performs the following basic functions:</span></span>  
  
- <span data-ttu-id="773dc-190">Zobrazí certifikáty, soubory CTL a CRL do konzoly.</span><span class="sxs-lookup"><span data-stu-id="773dc-190">Displays certificates, CTLs, and CRLs to the console.</span></span>  
  
- <span data-ttu-id="773dc-191">Přidá certifikáty, soubory CTL a CRL do úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="773dc-191">Adds certificates, CTLs, and CRLs to a certificate store.</span></span>  
  
- <span data-ttu-id="773dc-192">Odstraní certifikáty, soubory CTL a CRL z úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="773dc-192">Deletes certificates, CTLs, and CRLs from a certificate store.</span></span>  
  
- <span data-ttu-id="773dc-193">Uloží do souboru certifikát X.509, soubor CTL nebo CRL z úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="773dc-193">Saves an X.509 certificate, CTL, or CRL from a certificate store to a file.</span></span>  
  
 <span data-ttu-id="773dc-194">Certmgr.exe pracuje se dvěma typy úložišť certifikátů: **StoreFile** a System Store.</span><span class="sxs-lookup"><span data-stu-id="773dc-194">Certmgr.exe works with two types of certificate stores: **StoreFile** and system store.</span></span> <span data-ttu-id="773dc-195">Není nutné zadávat typ úložiště certifikátů. Certmgr.exe dokáže rozpoznat typ úložiště a vykonat příslušné operace.</span><span class="sxs-lookup"><span data-stu-id="773dc-195">It is not necessary to specify the type of certificate store; Certmgr.exe can identify the store type and perform the appropriate operations.</span></span>  
  
 <span data-ttu-id="773dc-196">Spuštěním nástroje Certmgr.exe bez určení jakýchkoli možností dojde ke spuštění modulu snap-in certmgr.msc, který obsahuje uživatelské rozhraní, které pomáhá s úlohami správy certifikátů, které jsou dostupné také z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="773dc-196">Running Certmgr.exe without specifying any options launches the certmgr.msc snap-in, which has a GUI that helps with the certificate management tasks that are also available from the command line.</span></span> <span data-ttu-id="773dc-197">Uživatelské rozhraní poskytuje průvodce importováním, který zkopíruje certifikáty, soubory CTL a CRL z disku do úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="773dc-197">The GUI provides an import wizard, which copies certificates, CTLs, and CRLs from your disk to a certificate store.</span></span>  
  
 <span data-ttu-id="773dc-198">Názvy úložišť certifikátu x509 pro `sourceStorename` parametry a můžete najít `destinationStorename` zkompilováním a spuštěním následujícího kódu.</span><span class="sxs-lookup"><span data-stu-id="773dc-198">You can find the names of X509Certificate stores for the `sourceStorename` and `destinationStorename` parameters by compiling and running the following code.</span></span>  
  
 [!code-csharp[Tools.CertMgr#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tools.certmgr/cs/storenames1.cs#1)]
 [!code-vb[Tools.CertMgr#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tools.certmgr/vb/storenames1.vb#1)]  
  
 <span data-ttu-id="773dc-199">Další informace o certifikátech najdete v tématu [práce s certifikáty](../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="773dc-199">For more information about certificates, see [Working with Certificates](../wcf/feature-details/working-with-certificates.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="773dc-200">Příklady</span><span class="sxs-lookup"><span data-stu-id="773dc-200">Examples</span></span>  
 <span data-ttu-id="773dc-201">Následující příkaz zobrazí výchozí úložiště `my` s názvem s podrobným výstupem.</span><span class="sxs-lookup"><span data-stu-id="773dc-201">The following command displays a default system store called `my` with verbose output.</span></span>  
  
```console  
certmgr /v /s my  
```  
  
 <span data-ttu-id="773dc-202">Následující příkaz přidá všechny certifikáty do souboru s názvem `myFile.ext` do nového souboru s názvem `newFile.ext` .</span><span class="sxs-lookup"><span data-stu-id="773dc-202">The following command adds all the certificates in a file called `myFile.ext` to a new file called `newFile.ext`.</span></span>  
  
```console  
certmgr /add /all /c myFile.ext newFile.ext  
```  
  
 <span data-ttu-id="773dc-203">Následující příkaz přidá certifikát do souboru s názvem `testcert.cer` do `my` úložiště systému.</span><span class="sxs-lookup"><span data-stu-id="773dc-203">The following command adds the certificate in a file named `testcert.cer` to the `my` system store.</span></span>  
  
```console  
certmgr /add /c testcert.cer /s my  
```  
  
 <span data-ttu-id="773dc-204">Následující příkaz přidá certifikát do souboru s názvem `TrustedCert.cer` do kořenového úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="773dc-204">The following command adds the certificate in a file named `TrustedCert.cer` to the root certificate store.</span></span>  
  
```console  
certmgr /c /add TrustedCert.cer /s root  
```  
  
 <span data-ttu-id="773dc-205">Následující příkaz uloží certifikát s běžným názvem `myCert` do `my` systémového úložiště do souboru s názvem `newCert.cer` .</span><span class="sxs-lookup"><span data-stu-id="773dc-205">The following command saves a certificate with the common name `myCert` in the `my` system store to a file called `newCert.cer`.</span></span>  
  
```console  
certmgr /add /c /n myCert /s my newCert.cer  
```  
  
 <span data-ttu-id="773dc-206">Následující příkaz odstraní všechny seznamy CTL v `my` úložišti systému a uloží výsledné úložiště do souboru s názvem `newStore.str` .</span><span class="sxs-lookup"><span data-stu-id="773dc-206">The following command deletes all CTLs in the `my` system store and saves the resulting store to a file called `newStore.str`.</span></span>  
  
```console  
certmgr /del /all /ctl /s my newStore.str  
```  
  
 <span data-ttu-id="773dc-207">Následující příkaz uloží certifikát do `my` systémového úložiště v souboru `newFile` .</span><span class="sxs-lookup"><span data-stu-id="773dc-207">The following command saves a certificate in the `my` system store in the file `newFile`.</span></span> <span data-ttu-id="773dc-208">Zobrazí se výzva k zadání čísla certifikátu z aplikace `my` do umístění `newFile` .</span><span class="sxs-lookup"><span data-stu-id="773dc-208">You will be prompted to enter the certificate number from `my` to put in `newFile`.</span></span>  
  
```console  
certmgr /put /c /s my newFile  
```  
  
## <a name="see-also"></a><span data-ttu-id="773dc-209">Viz také</span><span class="sxs-lookup"><span data-stu-id="773dc-209">See also</span></span>

- [<span data-ttu-id="773dc-210">Nástroje</span><span class="sxs-lookup"><span data-stu-id="773dc-210">Tools</span></span>](index.md)
- [<span data-ttu-id="773dc-211">Makecert.exe (Nástroj pro vytvoření certifikátu)</span><span class="sxs-lookup"><span data-stu-id="773dc-211">Makecert.exe (Certificate Creation Tool)</span></span>](/windows/desktop/SecCrypto/makecert)
- [<span data-ttu-id="773dc-212">Výzvy příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="773dc-212">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
