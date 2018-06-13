---
title: Ukázka FindPrivateKey - WCF
ms.date: 12/04/2017
helpviewer_keywords:
- FindPrivateKey
ms.assetid: 16b54116-0ceb-4413-af0c-753bb2a785a6
ms.openlocfilehash: 72e2f49ae7c39b4a0486ec053ff1164c2d833cbe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33501658"
---
# <a name="findprivatekey-sample"></a><span data-ttu-id="99144-102">Ukázka FindPrivateKey</span><span class="sxs-lookup"><span data-stu-id="99144-102">FindPrivateKey sample</span></span>

<span data-ttu-id="99144-103">Může být obtížné vyhledat umístění a název souboru privátního klíče přidruženého k určité X.509 certifikátu v úložišti certifikátů.</span><span class="sxs-lookup"><span data-stu-id="99144-103">It can be difficult to find the location and name of the private key file associated with a specific X.509 certificate in the certificate store.</span></span> <span data-ttu-id="99144-104">Nástroj FindPrivateKey.exe usnadňuje tento proces.</span><span class="sxs-lookup"><span data-stu-id="99144-104">The FindPrivateKey.exe tool facilitates this process.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="99144-105">FindPrivateKey je ukázka, která musí být kompilované před použitím.</span><span class="sxs-lookup"><span data-stu-id="99144-105">FindPrivateKey is a sample that needs to be compiled prior to use.</span></span> <span data-ttu-id="99144-106">Najdete v článku [pro sestavení projektu FindPrivateKey](#to-build-the-findprivatekey-project) část pokyny, jak sestavit nástroj FindPrivateKey.</span><span class="sxs-lookup"><span data-stu-id="99144-106">See the [To build the FindPrivateKey project](#to-build-the-findprivatekey-project) section for instructions on how to build the FindPrivateKey tool.</span></span>

<span data-ttu-id="99144-107">X.509 – certifikáty jsou nainstalované ve správcem nebo uživatelem na počítači.</span><span class="sxs-lookup"><span data-stu-id="99144-107">X.509 certificates are installed by an Administrator or any user in the machine.</span></span> <span data-ttu-id="99144-108">Certifikát však může být přístupné služby spuštěné pod jiným účtem.</span><span class="sxs-lookup"><span data-stu-id="99144-108">However, the certificate may be accessed by a service running under a different account.</span></span> <span data-ttu-id="99144-109">Například účet síťové služby.</span><span class="sxs-lookup"><span data-stu-id="99144-109">For example, the NETWORK SERVICE account.</span></span>

<span data-ttu-id="99144-110">Tento účet nemusí mít přístup k souboru privátního klíče, protože certifikát nebyl nainstalován v souladu se původně.</span><span class="sxs-lookup"><span data-stu-id="99144-110">This account may not have access to the private key file because the certificate was not installed by it originally.</span></span> <span data-ttu-id="99144-111">Nástroj FindPrivateKey vám dává umístění soubor privátního klíče daný certifikát X.509.</span><span class="sxs-lookup"><span data-stu-id="99144-111">The FindPrivateKey tool gives you the location of a given X.509 Certificate's private key file.</span></span> <span data-ttu-id="99144-112">Můžete přidat oprávnění nebo odeberte oprávnění k tomuto souboru znáte umístění konkrétní certifikáty X.509 soubor privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="99144-112">You can add permissions or remove permissions to this file once you know the location of the particular X.509 certificates' private key file.</span></span>

<span data-ttu-id="99144-113">Ukázky, které používají certifikáty pro zabezpečení použít nástroj FindPrivateKey v *Setup.bat* souboru.</span><span class="sxs-lookup"><span data-stu-id="99144-113">The samples that use certificates for security use the FindPrivateKey tool in the *Setup.bat* file.</span></span> <span data-ttu-id="99144-114">Jakmile byl nalezen soubor privátního klíče, můžete použít jiné nástroje, jako *Cacls.exe* nastavit příslušná přístupová práva do souboru.</span><span class="sxs-lookup"><span data-stu-id="99144-114">Once the private key file has been found, you can use other tools such as *Cacls.exe* to set the appropriate access rights onto the file.</span></span>

<span data-ttu-id="99144-115">Při spuštění služby Windows Communication Foundation (WCF) pod uživatelským účtem, například vlastním hostováním spustitelný soubor, ujistěte se, že uživatelský účet má oprávnění jen pro čtení k souboru.</span><span class="sxs-lookup"><span data-stu-id="99144-115">When running a Windows Communication Foundation (WCF) service under a user account, such as a self-hosted executable, ensure that the user account has read-only access to the file.</span></span> <span data-ttu-id="99144-116">Při spuštění služby WCF v rámci Internetové informační služby (IIS) jsou výchozí účty, které se spouští služba NETWORK SERVICE ve službě IIS 7 a starší verze nebo identita fondu aplikací služby IIS 7.5 a novější verze.</span><span class="sxs-lookup"><span data-stu-id="99144-116">When running a WCF service under Internet Information Services (IIS) the default accounts that the service runs under are the NETWORK SERVICE on IIS 7 and earlier versions, or Application Pool Identity on IIS 7.5 and later versions.</span></span> <span data-ttu-id="99144-117">Další informace najdete v tématu [identity fondu aplikací součásti](/iis/manage/configuring-security/application-pool-identities).</span><span class="sxs-lookup"><span data-stu-id="99144-117">For more information, see [Application Pool Identities](/iis/manage/configuring-security/application-pool-identities).</span></span>

## <a name="examples"></a><span data-ttu-id="99144-118">Příklady</span><span class="sxs-lookup"><span data-stu-id="99144-118">Examples</span></span>

<span data-ttu-id="99144-119">Při přístupu k certifikátu, pro které proces nemá oprávnění pro čtení, zobrazí se zprávou výjimky podobně jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="99144-119">When accessing a certificate for which the process doesn't have read privilege, you see an exception message similar to the following example:</span></span>

```
System.ArgumentException was unhandled
Message="The certificate 'CN=localhost' must have a private key that is capable of key exchange.  The process must have access rights for the private key."
Source="System.ServiceModel"
```

<span data-ttu-id="99144-120">V takovém případě najít soubor privátního klíče pomocí nástroje FindPrivateKey a nastavte přístupu pro proces, který je služba spuštěná v části.</span><span class="sxs-lookup"><span data-stu-id="99144-120">When this occurs, use the FindPrivateKey tool to find the private key file, and then set the access right for the process that the service is running under.</span></span> <span data-ttu-id="99144-121">Například to lze provést pomocí nástroje Cacls.exe jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="99144-121">For example, this can be done with the Cacls.exe tool as shown in the following example:</span></span>

```
cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R
```

#### <a name="to-build-the-findprivatekey-project"></a><span data-ttu-id="99144-122">Pro sestavení projektu FindPrivateKey</span><span class="sxs-lookup"><span data-stu-id="99144-122">To build the FindPrivateKey project</span></span>

<span data-ttu-id="99144-123">Je možné stáhnout projektu [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459).</span><span class="sxs-lookup"><span data-stu-id="99144-123">To download the project, visit [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459).</span></span>

1. <span data-ttu-id="99144-124">Otevřete [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] a přejděte do *WF_WCF_Samples\WCF\Setup\FindPrivateKey\CS* složku s umístěním adresáře, kam jste nainstalovali vzorku.</span><span class="sxs-lookup"><span data-stu-id="99144-124">Open [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] and navigate to the *WF_WCF_Samples\WCF\Setup\FindPrivateKey\CS* folder under the directory location where you installed the sample.</span></span>

2. <span data-ttu-id="99144-125">Dvakrát klikněte na ikonu soubor .sln k otevření souboru v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="99144-125">Double-click the .sln file icon to open the file in Visual Studio.</span></span>

3. <span data-ttu-id="99144-126">V **sestavení** nabídce vyberte možnost **znovu sestavit řešení**.</span><span class="sxs-lookup"><span data-stu-id="99144-126">In the **Build** menu, select **Rebuild Solution**.</span></span>

4. <span data-ttu-id="99144-127">Sestavování řešení vygeneruje soubor: FindPrivateKey.exe.</span><span class="sxs-lookup"><span data-stu-id="99144-127">Building the solution generates the file: FindPrivateKey.exe.</span></span>

## <a name="conventionscommand-line-entries"></a><span data-ttu-id="99144-128">Konvence – položky příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="99144-128">Conventions—Command-Line entries</span></span>

 <span data-ttu-id="99144-129">"[*možnost*]" představuje volitelný sadu parametrů.</span><span class="sxs-lookup"><span data-stu-id="99144-129">"[*option*]" represents an optional set of parameters.</span></span>

 <span data-ttu-id="99144-130">"{*možnost*}" představuje sadu parametrů povinné.</span><span class="sxs-lookup"><span data-stu-id="99144-130">"{*option*}" represents a mandatory set of parameters.</span></span>

 <span data-ttu-id="99144-131">"*možnost 1* &#124; *option2*" představuje volba mezi sady možností.</span><span class="sxs-lookup"><span data-stu-id="99144-131">"*option1* &#124; *option2*" represents a choice between sets of options.</span></span>

 <span data-ttu-id="99144-132">"\<*hodnotu*>" představuje hodnotu parametru, které je třeba zadat.</span><span class="sxs-lookup"><span data-stu-id="99144-132">"\<*value*>" represents a parameter value to be entered.</span></span>

## <a name="usage"></a><span data-ttu-id="99144-133">Použití</span><span class="sxs-lookup"><span data-stu-id="99144-133">Usage</span></span>

```
FindPrivateKey <storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]
```

<span data-ttu-id="99144-134">Kde:</span><span class="sxs-lookup"><span data-stu-id="99144-134">Where:</span></span>

```
       <subjectName> The subject name of the certificate
       <thumbprint>  The thumbprint of the certificate (You can use the Certmgr.exe tool to find this)
       -f            output file name only
       -d            output directory only
       -a            output absolute file name
```

<span data-ttu-id="99144-135">Pokud nejsou zadány žádné parametry příkazového řádku, se zobrazí tento text nápovědy.</span><span class="sxs-lookup"><span data-stu-id="99144-135">If no parameters are specified at the command prompt, then this help text is displayed.</span></span>

## <a name="examples"></a><span data-ttu-id="99144-136">Příklady</span><span class="sxs-lookup"><span data-stu-id="99144-136">Examples</span></span>

<span data-ttu-id="99144-137">Tento příklad vyhledá název souboru certifikátu s názvem subjektu "CN = localhost", v osobním úložišti aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="99144-137">This example finds the filename of the certificate with a subject name of "CN=localhost", in the Personal store of the Current User.</span></span>

```
FindPrivateKey My CurrentUser -n "CN=localhost"
```

<span data-ttu-id="99144-138">Tento příklad vyhledá název souboru certifikátu s názvem subjektu "CN = localhost", v osobní uložení aktuálního uživatele a výstupní cesta k adresáři úplná.</span><span class="sxs-lookup"><span data-stu-id="99144-138">This example finds the filename of the certificate with a subject name of "CN=localhost", in the Personal store of the Current User and output the full directory path.</span></span>

```
FindPrivateKey My CurrentUser -n "CN=localhost" -a
```

<span data-ttu-id="99144-139">Tento příklad vyhledá název souboru certifikátu s kryptografickým otiskem "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1 d 6b 52", v osobním úložišti místního počítače.</span><span class="sxs-lookup"><span data-stu-id="99144-139">This example finds the filename of the certificate with a thumbprint of "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52", in the Personal store of the Local Computer.</span></span>

```
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52"
```
