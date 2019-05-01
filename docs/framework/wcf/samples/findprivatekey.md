---
title: Ukázkový FindPrivateKey – WCF
ms.date: 12/04/2017
helpviewer_keywords:
- FindPrivateKey
ms.assetid: 16b54116-0ceb-4413-af0c-753bb2a785a6
ms.openlocfilehash: 72e2f49ae7c39b4a0486ec053ff1164c2d833cbe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61990090"
---
# <a name="findprivatekey-sample"></a><span data-ttu-id="84bbe-102">Ukázka FindPrivateKey</span><span class="sxs-lookup"><span data-stu-id="84bbe-102">FindPrivateKey sample</span></span>

<span data-ttu-id="84bbe-103">Může být obtížné najít umístění a název souboru privátního klíče přidružené k určité certifikát X.509 v úložišti certifikátů.</span><span class="sxs-lookup"><span data-stu-id="84bbe-103">It can be difficult to find the location and name of the private key file associated with a specific X.509 certificate in the certificate store.</span></span> <span data-ttu-id="84bbe-104">Nástroj FindPrivateKey.exe usnadňuje tento proces.</span><span class="sxs-lookup"><span data-stu-id="84bbe-104">The FindPrivateKey.exe tool facilitates this process.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="84bbe-105">FindPrivateKey je příklad, který má být zkompilovaný před použitím.</span><span class="sxs-lookup"><span data-stu-id="84bbe-105">FindPrivateKey is a sample that needs to be compiled prior to use.</span></span> <span data-ttu-id="84bbe-106">Najdete v článku [sestavit projekt FindPrivateKey](#to-build-the-findprivatekey-project) pokyny o tom, jak nástroj FindPrivateKey sestavení.</span><span class="sxs-lookup"><span data-stu-id="84bbe-106">See the [To build the FindPrivateKey project](#to-build-the-findprivatekey-project) section for instructions on how to build the FindPrivateKey tool.</span></span>

<span data-ttu-id="84bbe-107">Správce nebo všechny uživatele v počítači jsou nainstalovány certifikáty X.509.</span><span class="sxs-lookup"><span data-stu-id="84bbe-107">X.509 certificates are installed by an Administrator or any user in the machine.</span></span> <span data-ttu-id="84bbe-108">Certifikát, ale můžou být dostupné služby spuštěné pod jiným účtem.</span><span class="sxs-lookup"><span data-stu-id="84bbe-108">However, the certificate may be accessed by a service running under a different account.</span></span> <span data-ttu-id="84bbe-109">Například účet NETWORK SERVICE.</span><span class="sxs-lookup"><span data-stu-id="84bbe-109">For example, the NETWORK SERVICE account.</span></span>

<span data-ttu-id="84bbe-110">Tento účet nesmí mít přístup k souboru privátního klíče, protože certifikát nebyl nainstalován jím původně.</span><span class="sxs-lookup"><span data-stu-id="84bbe-110">This account may not have access to the private key file because the certificate was not installed by it originally.</span></span> <span data-ttu-id="84bbe-111">Nástroj FindPrivateKey poskytuje umístění souboru s privátním klíčem daný certifikát X.509.</span><span class="sxs-lookup"><span data-stu-id="84bbe-111">The FindPrivateKey tool gives you the location of a given X.509 Certificate's private key file.</span></span> <span data-ttu-id="84bbe-112">Můžete přidat oprávnění nebo odebrat oprávnění k tomuto souboru znáte umístění souboru s privátním klíčem konkrétní certifikátů X.509.</span><span class="sxs-lookup"><span data-stu-id="84bbe-112">You can add permissions or remove permissions to this file once you know the location of the particular X.509 certificates' private key file.</span></span>

<span data-ttu-id="84bbe-113">Ukázky, které používají certifikáty pro zabezpečení, použijte nástroj FindPrivateKey v *Setup.bat* souboru.</span><span class="sxs-lookup"><span data-stu-id="84bbe-113">The samples that use certificates for security use the FindPrivateKey tool in the *Setup.bat* file.</span></span> <span data-ttu-id="84bbe-114">Jakmile byla nalezena souboru s privátním klíčem, můžete použít jiné nástroje, jako *Cacls.exe* nastavit příslušná přístupová práva do souboru.</span><span class="sxs-lookup"><span data-stu-id="84bbe-114">Once the private key file has been found, you can use other tools such as *Cacls.exe* to set the appropriate access rights onto the file.</span></span>

<span data-ttu-id="84bbe-115">Při spuštění služby Windows Communication Foundation (WCF) uživatelského účtu, jako je například v místním prostředí spustitelný soubor, ujistěte se, že uživatelský účet má k souboru přístup jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="84bbe-115">When running a Windows Communication Foundation (WCF) service under a user account, such as a self-hosted executable, ensure that the user account has read-only access to the file.</span></span> <span data-ttu-id="84bbe-116">Při spuštění služby WCF v rámci Internetové informační služby (IIS) jsou výchozí účty, které je služba spuštěna pod síťové služby na službě IIS 7 a starší nebo identitu fondu aplikací služby IIS 7.5 a novější verze.</span><span class="sxs-lookup"><span data-stu-id="84bbe-116">When running a WCF service under Internet Information Services (IIS) the default accounts that the service runs under are the NETWORK SERVICE on IIS 7 and earlier versions, or Application Pool Identity on IIS 7.5 and later versions.</span></span> <span data-ttu-id="84bbe-117">Další informace najdete v tématu [identity fondu aplikací součásti](/iis/manage/configuring-security/application-pool-identities).</span><span class="sxs-lookup"><span data-stu-id="84bbe-117">For more information, see [Application Pool Identities](/iis/manage/configuring-security/application-pool-identities).</span></span>

## <a name="examples"></a><span data-ttu-id="84bbe-118">Příklady</span><span class="sxs-lookup"><span data-stu-id="84bbe-118">Examples</span></span>

<span data-ttu-id="84bbe-119">Při přístupu k certifikátu, pro kterou proces nemá oprávnění pro čtení, zobrazí zprávu o výjimce, podobně jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="84bbe-119">When accessing a certificate for which the process doesn't have read privilege, you see an exception message similar to the following example:</span></span>

```
System.ArgumentException was unhandled
Message="The certificate 'CN=localhost' must have a private key that is capable of key exchange.  The process must have access rights for the private key."
Source="System.ServiceModel"
```

<span data-ttu-id="84bbe-120">Když k tomu dojde, použijte nástroj FindPrivateKey najít soubor privátního klíče a nastavte přístup pro proces, který je služba spuštěná pod.</span><span class="sxs-lookup"><span data-stu-id="84bbe-120">When this occurs, use the FindPrivateKey tool to find the private key file, and then set the access right for the process that the service is running under.</span></span> <span data-ttu-id="84bbe-121">Například to můžete udělat pomocí nástroje Cacls.exe jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="84bbe-121">For example, this can be done with the Cacls.exe tool as shown in the following example:</span></span>

```
cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R
```

#### <a name="to-build-the-findprivatekey-project"></a><span data-ttu-id="84bbe-122">Sestavit projekt FindPrivateKey</span><span class="sxs-lookup"><span data-stu-id="84bbe-122">To build the FindPrivateKey project</span></span>

<span data-ttu-id="84bbe-123">Stáhněte si projekt, najdete v tématu [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459).</span><span class="sxs-lookup"><span data-stu-id="84bbe-123">To download the project, visit [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459).</span></span>

1. <span data-ttu-id="84bbe-124">Otevřít [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] a přejděte *WF_WCF_Samples\WCF\Setup\FindPrivateKey\CS* složku v umístění adresáře, kam jste nainstalovali vzorku.</span><span class="sxs-lookup"><span data-stu-id="84bbe-124">Open [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] and navigate to the *WF_WCF_Samples\WCF\Setup\FindPrivateKey\CS* folder under the directory location where you installed the sample.</span></span>

2. <span data-ttu-id="84bbe-125">Dvakrát klikněte na ikonu souboru .sln k otevření souboru v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="84bbe-125">Double-click the .sln file icon to open the file in Visual Studio.</span></span>

3. <span data-ttu-id="84bbe-126">V **sestavení** nabídce vyberte možnost **znovu sestavit řešení**.</span><span class="sxs-lookup"><span data-stu-id="84bbe-126">In the **Build** menu, select **Rebuild Solution**.</span></span>

4. <span data-ttu-id="84bbe-127">Sestavování řešení se vygeneruje soubor: FindPrivateKey.exe.</span><span class="sxs-lookup"><span data-stu-id="84bbe-127">Building the solution generates the file: FindPrivateKey.exe.</span></span>

## <a name="conventionscommand-line-entries"></a><span data-ttu-id="84bbe-128">Konvence – položky příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="84bbe-128">Conventions—Command-Line entries</span></span>

 <span data-ttu-id="84bbe-129">"[*možnost*]" představuje volitelný sadu parametrů.</span><span class="sxs-lookup"><span data-stu-id="84bbe-129">"[*option*]" represents an optional set of parameters.</span></span>

 <span data-ttu-id="84bbe-130">"{*možnost*}" představuje povinný sadu parametrů.</span><span class="sxs-lookup"><span data-stu-id="84bbe-130">"{*option*}" represents a mandatory set of parameters.</span></span>

 <span data-ttu-id="84bbe-131">"*možnost1* &#124; *možnost2*" představuje možností volby mezi sadu možností.</span><span class="sxs-lookup"><span data-stu-id="84bbe-131">"*option1* &#124; *option2*" represents a choice between sets of options.</span></span>

 <span data-ttu-id="84bbe-132">"\<*hodnotu*>" představuje hodnotu parametru k zapsání.</span><span class="sxs-lookup"><span data-stu-id="84bbe-132">"\<*value*>" represents a parameter value to be entered.</span></span>

## <a name="usage"></a><span data-ttu-id="84bbe-133">Použití</span><span class="sxs-lookup"><span data-stu-id="84bbe-133">Usage</span></span>

```
FindPrivateKey <storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]
```

<span data-ttu-id="84bbe-134">kde:</span><span class="sxs-lookup"><span data-stu-id="84bbe-134">Where:</span></span>

```
       <subjectName> The subject name of the certificate
       <thumbprint>  The thumbprint of the certificate (You can use the Certmgr.exe tool to find this)
       -f            output file name only
       -d            output directory only
       -a            output absolute file name
```

<span data-ttu-id="84bbe-135">Pokud nejsou zadány žádné parametry příkazového řádku, se zobrazí tento text nápovědy.</span><span class="sxs-lookup"><span data-stu-id="84bbe-135">If no parameters are specified at the command prompt, then this help text is displayed.</span></span>

## <a name="examples"></a><span data-ttu-id="84bbe-136">Příklady</span><span class="sxs-lookup"><span data-stu-id="84bbe-136">Examples</span></span>

<span data-ttu-id="84bbe-137">Tento příklad vyhledá název souboru certifikátu se název předmětu "CN = localhost", v osobním úložišti aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="84bbe-137">This example finds the filename of the certificate with a subject name of "CN=localhost", in the Personal store of the Current User.</span></span>

```
FindPrivateKey My CurrentUser -n "CN=localhost"
```

<span data-ttu-id="84bbe-138">Tento příklad vyhledá název souboru certifikátu se název předmětu "CN = localhost", v osobní uložení aktuálního uživatele a výstupní cesta k adresáři úplné.</span><span class="sxs-lookup"><span data-stu-id="84bbe-138">This example finds the filename of the certificate with a subject name of "CN=localhost", in the Personal store of the Current User and output the full directory path.</span></span>

```
FindPrivateKey My CurrentUser -n "CN=localhost" -a
```

<span data-ttu-id="84bbe-139">Tento příklad vyhledá název souboru certifikátu s kryptografickým otiskem z "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1 d 6b 52", v osobním úložišti místního počítače.</span><span class="sxs-lookup"><span data-stu-id="84bbe-139">This example finds the filename of the certificate with a thumbprint of "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52", in the Personal store of the Local Computer.</span></span>

```
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52"
```
