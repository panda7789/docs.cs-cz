---
title: FindPrivateKey
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: FindPrivateKey
ms.assetid: 16b54116-0ceb-4413-af0c-753bb2a785a6
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 81ca357ccdcbe76f36f3ba56caf2013a80143728
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="findprivatekey"></a><span data-ttu-id="7d7d3-102">FindPrivateKey</span><span class="sxs-lookup"><span data-stu-id="7d7d3-102">FindPrivateKey</span></span>
<span data-ttu-id="7d7d3-103">Může být obtížné vyhledat umístění a název souboru privátního klíče přidruženého k určité X.509 certifikátu v úložišti certifikátů.</span><span class="sxs-lookup"><span data-stu-id="7d7d3-103">It can be difficult to find the location and name of the private key file associated with a specific X.509 certificate in the certificate store.</span></span> <span data-ttu-id="7d7d3-104">Nástroj FindPrivateKey.exe usnadňuje tento proces.</span><span class="sxs-lookup"><span data-stu-id="7d7d3-104">The FindPrivateKey.exe tool facilitates this process.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7d7d3-105">FindPrivateKey je ukázka, která musí být kompilované před použitím.</span><span class="sxs-lookup"><span data-stu-id="7d7d3-105">FindPrivateKey is a sample that needs to be compiled prior to use.</span></span> <span data-ttu-id="7d7d3-106">Najdete v části "pro sestavení projektu FindPrivateKey" části níže pokyny o tom, jak sestavit nástroj FindPrivateKey.</span><span class="sxs-lookup"><span data-stu-id="7d7d3-106">See the "To build the FindPrivateKey project" section below for instructions on how to build the FindPrivateKey tool.</span></span>  
  
 <span data-ttu-id="7d7d3-107">X.509 – certifikáty jsou nainstalované ve správcem nebo uživatelem na počítači.</span><span class="sxs-lookup"><span data-stu-id="7d7d3-107">X.509 certificates are installed by an Administrator or any user in the machine.</span></span> <span data-ttu-id="7d7d3-108">Certifikát může být ale přístupné služby spuštěné pod jiným účtem (například ASPNET na [!INCLUDE[wxp](../../../../includes/wxp-md.md)] nebo účty síťové služby v [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="7d7d3-108">However the certificate may be accessed by a service running under a different account (for example, the ASPNET on [!INCLUDE[wxp](../../../../includes/wxp-md.md)] or the NETWORK SERVICE accounts on [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]).</span></span>  
  
 <span data-ttu-id="7d7d3-109">Tento účet nemusí mít přístup k souboru privátního klíče, protože certifikát nebyl nainstalován v souladu se původně.</span><span class="sxs-lookup"><span data-stu-id="7d7d3-109">This account may not have access to the private key file because the certificate was not installed by it originally.</span></span> <span data-ttu-id="7d7d3-110">Nástroj FindPrivateKey vám dává umístění soubor privátního klíče daný certifikát X.509.</span><span class="sxs-lookup"><span data-stu-id="7d7d3-110">The FindPrivateKey tool gives you the location of a given X.509 Certificate's private key file.</span></span> <span data-ttu-id="7d7d3-111">Můžete přidat oprávnění nebo odeberte oprávnění k tomuto souboru znáte umístění konkrétní certifikáty X.509 soubor privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="7d7d3-111">You can add permissions or remove permissions to this file once you know the location of the particular X.509 certificates' private key file.</span></span>  
  
 <span data-ttu-id="7d7d3-112">Ukázky, které používají certifikáty pro zabezpečení použít nástroj FindPrivateKey v souboru Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="7d7d3-112">The samples that use certificates for security use the FindPrivateKey tool in the Setup.bat file.</span></span> <span data-ttu-id="7d7d3-113">Jakmile nebyl nalezen soubor privátního klíče, že které můžete použít jiné nástroje, například Cacls.exe nastavit příslušná přístupová práva do souboru.</span><span class="sxs-lookup"><span data-stu-id="7d7d3-113">Once the private key file has been found you can use other tools such as Cacls.exe to set the appropriate access rights onto the file.</span></span>  
  
 <span data-ttu-id="7d7d3-114">Při spuštění [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby pod uživatelským účtem, například vlastním hostováním spustitelný soubor, ujistěte se, že uživatelský účet má oprávnění jen pro čtení k souboru.</span><span class="sxs-lookup"><span data-stu-id="7d7d3-114">When running a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service under a user account, such as a self-hosted executable, ensure that the user account has read-only access to the file.</span></span> <span data-ttu-id="7d7d3-115">Při spuštění [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby v rámci Internetové informační služby (IIS) výchozí účty, které se spouští služba jsou ASPNET na [!INCLUDE[wxp](../../../../includes/wxp-md.md)] nebo síťové službě v [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], který ve výchozím nastavení nemají přístup k souboru privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="7d7d3-115">When running a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service under Internet Information Services (IIS) the default accounts that the service runs under are the ASPNET on [!INCLUDE[wxp](../../../../includes/wxp-md.md)] or the NETWORK SERVICE on [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], which by default do not have access to the private key file.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="7d7d3-116">Příklady</span><span class="sxs-lookup"><span data-stu-id="7d7d3-116">Examples</span></span>  
 <span data-ttu-id="7d7d3-117">Při přístupu k certifikátu, pro které proces nemá oprávnění pro čtení, zobrazí se zprávou výjimky podobně jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="7d7d3-117">When accessing a certificate for which the process does not have read privilege, you see an exception message similar to the following example.</span></span>  
  
```  
System.ArgumentException was unhandled  
Message="The certificate 'CN=localhost' must have a private key that is capable of key exchange.  The process must have access rights for the private key."  
Source="System.ServiceModel"  
```  
  
 <span data-ttu-id="7d7d3-118">V takovém případě použijte nástroj FindPrivateKey Pokud chcete najít soubor privátního klíče a potom nastavte přístupu pro proces, který je služba spuštěná v části.</span><span class="sxs-lookup"><span data-stu-id="7d7d3-118">When this occurs use the FindPrivateKey tool to find the private key file and then set the access right for the process that the service is running under.</span></span> <span data-ttu-id="7d7d3-119">Například to lze provést pomocí nástroje Cacls.exe jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="7d7d3-119">For example, this can be done with the Cacls.exe tool as shown in the following example.</span></span>  
  
```  
cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R  
```  
  
#### <a name="to-build-the-findprivatekey-project"></a><span data-ttu-id="7d7d3-120">Pro sestavení projektu FindPrivateKey</span><span class="sxs-lookup"><span data-stu-id="7d7d3-120">To build the FindPrivateKey project</span></span>  
  
1.  <span data-ttu-id="7d7d3-121">Otevřete [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] a přejděte do konkrétní jazyk podadresáře v části umístění adresáře, kam jste nainstalovali vzorku.</span><span class="sxs-lookup"><span data-stu-id="7d7d3-121">Open [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] and navigate to the language-specific subdirectory under the directory location where you installed the sample.</span></span>  
  
2.  <span data-ttu-id="7d7d3-122">Dvakrát klikněte na ikonu soubor .sln k otevření souboru v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7d7d3-122">Double-click the .sln file icon to open the file in Visual Studio.</span></span>  
  
3.  <span data-ttu-id="7d7d3-123">V **sestavení** nabídce vyberte možnost **znovu sestavit řešení**.</span><span class="sxs-lookup"><span data-stu-id="7d7d3-123">In the **Build** menu, select **Rebuild Solution**.</span></span> <span data-ttu-id="7d7d3-124">Soubory programu klienta jsou vytvořeny tak client\bin a soubory programu služby jsou vytvořeny tak service\bin.</span><span class="sxs-lookup"><span data-stu-id="7d7d3-124">The client program files are built to client\bin and the service program files are built to service\bin.</span></span>  
  
4.  <span data-ttu-id="7d7d3-125">Sestavování řešení vygeneruje soubor: FindPrivateKey.exe.</span><span class="sxs-lookup"><span data-stu-id="7d7d3-125">Building the solution generates the file: FindPrivateKey.exe.</span></span>  
  
## <a name="conventionscommand-line-entries"></a><span data-ttu-id="7d7d3-126">Konvence – položky příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="7d7d3-126">Conventions—Command-Line Entries</span></span>  
 <span data-ttu-id="7d7d3-127">"[*možnost*]" představuje volitelný sadu parametrů.</span><span class="sxs-lookup"><span data-stu-id="7d7d3-127">"[*option*]" represents an optional set of parameters.</span></span>  
  
 <span data-ttu-id="7d7d3-128">"{*možnost*}" představuje sadu parametrů povinné.</span><span class="sxs-lookup"><span data-stu-id="7d7d3-128">"{*option*}" represents a mandatory set of parameters.</span></span>  
  
 <span data-ttu-id="7d7d3-129">"*možnost 1* &#124; *option2*"představuje volba mezi sady možností.</span><span class="sxs-lookup"><span data-stu-id="7d7d3-129">"*option1* &#124; *option2*" represents a choice between sets of options.</span></span>  
  
 <span data-ttu-id="7d7d3-130">"\<*hodnotu*>" představuje hodnotu parametru, které je třeba zadat.</span><span class="sxs-lookup"><span data-stu-id="7d7d3-130">"\<*value*>" represents a parameter value to be entered.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="7d7d3-131">Použití</span><span class="sxs-lookup"><span data-stu-id="7d7d3-131">Usage</span></span>  
  
```  
FindPrivateKey <storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]  
```  
  
 <span data-ttu-id="7d7d3-132">Kde:</span><span class="sxs-lookup"><span data-stu-id="7d7d3-132">Where:</span></span>  
  
```  
       <subjectName> The subject name of the certificate  
       <thumbprint>  The thumbprint of the certificate (You can use the Certmgr.exe tool to find this)  
       -f            output file name only  
       -d            output directory only  
       -a            output absolute file name  
```  
  
 <span data-ttu-id="7d7d3-133">Pokud nejsou zadány žádné parametry na příkazovém řádku se zobrazí tento text nápovědy.</span><span class="sxs-lookup"><span data-stu-id="7d7d3-133">If no parameters are specified at the command prompt then this help text is displayed.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="7d7d3-134">Příklady</span><span class="sxs-lookup"><span data-stu-id="7d7d3-134">Examples</span></span>  
 <span data-ttu-id="7d7d3-135">Tento příklad vyhledá název souboru certifikátu s názvem subjektu "CN = localhost", v osobním úložišti aktuální User.FindPrivateKey Moje CurrentUser - n "CN = localhost".</span><span class="sxs-lookup"><span data-stu-id="7d7d3-135">This example finds the filename of the certificate with a subject name of "CN=localhost", in the Personal store of the Current User.FindPrivateKey My CurrentUser -n "CN=localhost".</span></span>  
  
 <span data-ttu-id="7d7d3-136">Tento příklad vyhledá název souboru certifikátu s názvem subjektu "CN = localhost", v osobní uložení aktuálního a výstupní cesta k adresáři úplné.</span><span class="sxs-lookup"><span data-stu-id="7d7d3-136">This example finds the filename of the certificate with a subject name of "CN=localhost", in the Personal store of the Current and output the full directory path.</span></span>  
  
```  
User.FindPrivateKey My CurrentUser -n "CN=localhost" -a  
```  
  
 <span data-ttu-id="7d7d3-137">Tento příklad vyhledá název souboru certifikátu s kryptografickým otiskem "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1 d 6b 52", v osobním úložišti místního počítače.</span><span class="sxs-lookup"><span data-stu-id="7d7d3-137">This example finds the filename of the certificate with a thumbprint of "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52", in the Personal store of the Local Computer.</span></span>  
  
```  
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" –c  
```  
  
## <a name="see-also"></a><span data-ttu-id="7d7d3-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="7d7d3-138">See Also</span></span>
