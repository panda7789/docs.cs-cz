---
title: Ukázka FindPrivateKey
ms.date: 12/04/2017
helpviewer_keywords:
- FindPrivateKey
ms.assetid: 16b54116-0ceb-4413-af0c-753bb2a785a6
ms.openlocfilehash: 0ed1e5e81a5d2f7f3586e5dce306e8244b5ebd48
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346020"
---
# <a name="findprivatekey-sample"></a><span data-ttu-id="bbd68-102">Ukázka FindPrivateKey</span><span class="sxs-lookup"><span data-stu-id="bbd68-102">FindPrivateKey sample</span></span>

<span data-ttu-id="bbd68-103">Může být obtížné najít umístění a název souboru privátního klíče přidruženého k určitému certifikátu X. 509 v úložišti certifikátů.</span><span class="sxs-lookup"><span data-stu-id="bbd68-103">It can be difficult to find the location and name of the private key file associated with a specific X.509 certificate in the certificate store.</span></span> <span data-ttu-id="bbd68-104">Nástroj FindPrivateKey. exe Tento proces usnadňuje.</span><span class="sxs-lookup"><span data-stu-id="bbd68-104">The FindPrivateKey.exe tool facilitates this process.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bbd68-105">FindPrivateKey je ukázka, kterou je třeba před použitím zkompilovat.</span><span class="sxs-lookup"><span data-stu-id="bbd68-105">FindPrivateKey is a sample that needs to be compiled prior to use.</span></span> <span data-ttu-id="bbd68-106">Pokyny k vytvoření nástroje FindPrivateKey najdete v části [Vytvoření projektu FindPrivateKey](#to-build-the-findprivatekey-project) .</span><span class="sxs-lookup"><span data-stu-id="bbd68-106">See the [To build the FindPrivateKey project](#to-build-the-findprivatekey-project) section for instructions on how to build the FindPrivateKey tool.</span></span>

<span data-ttu-id="bbd68-107">Certifikáty X. 509 jsou nainstalovány správcem nebo jakýmkoli uživatelem v počítači.</span><span class="sxs-lookup"><span data-stu-id="bbd68-107">X.509 certificates are installed by an Administrator or any user in the machine.</span></span> <span data-ttu-id="bbd68-108">K certifikátu ale může mít přístup služba spuštěná v jiném účtu.</span><span class="sxs-lookup"><span data-stu-id="bbd68-108">However, the certificate may be accessed by a service running under a different account.</span></span> <span data-ttu-id="bbd68-109">Například účet síťové služby.</span><span class="sxs-lookup"><span data-stu-id="bbd68-109">For example, the NETWORK SERVICE account.</span></span>

<span data-ttu-id="bbd68-110">Tento účet nemusí mít přístup k souboru privátního klíče, protože certifikát nebyl původně nainstalován.</span><span class="sxs-lookup"><span data-stu-id="bbd68-110">This account may not have access to the private key file because the certificate was not installed by it originally.</span></span> <span data-ttu-id="bbd68-111">Nástroj FindPrivateKey poskytuje umístění daného souboru privátního klíče certifikátu X. 509.</span><span class="sxs-lookup"><span data-stu-id="bbd68-111">The FindPrivateKey tool gives you the location of a given X.509 Certificate's private key file.</span></span> <span data-ttu-id="bbd68-112">Jakmile budete znát umístění konkrétního souboru privátního klíče certifikátů X. 509, můžete oprávnění k tomuto souboru přidat nebo je z něj odebrat.</span><span class="sxs-lookup"><span data-stu-id="bbd68-112">You can add permissions or remove permissions to this file once you know the location of the particular X.509 certificates' private key file.</span></span>

<span data-ttu-id="bbd68-113">V ukázkách, které používají certifikáty k zabezpečení, se používá nástroj FindPrivateKey v souboru *Setup. bat* .</span><span class="sxs-lookup"><span data-stu-id="bbd68-113">The samples that use certificates for security use the FindPrivateKey tool in the *Setup.bat* file.</span></span> <span data-ttu-id="bbd68-114">Po nalezení souboru privátního klíče můžete použít jiné nástroje, jako je například *cacls. exe* , a nastavit tak příslušná přístupová práva na daný soubor.</span><span class="sxs-lookup"><span data-stu-id="bbd68-114">Once the private key file has been found, you can use other tools such as *Cacls.exe* to set the appropriate access rights onto the file.</span></span>

<span data-ttu-id="bbd68-115">Při spuštění služby Windows Communication Foundation (WCF) pod uživatelským účtem, jako je například spustitelný soubor v místním prostředí, zajistěte, aby měl uživatelský účet k souboru přístup jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="bbd68-115">When running a Windows Communication Foundation (WCF) service under a user account, such as a self-hosted executable, ensure that the user account has read-only access to the file.</span></span> <span data-ttu-id="bbd68-116">Při spuštění služby WCF pod Internetová informační služba (IIS) výchozí účty, ve kterých je služba spuštěná, jsou síťové služby ve službě IIS 7 a starší verze nebo identita fondu aplikací ve službě IIS 7,5 a novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="bbd68-116">When running a WCF service under Internet Information Services (IIS) the default accounts that the service runs under are the NETWORK SERVICE on IIS 7 and earlier versions, or Application Pool Identity on IIS 7.5 and later versions.</span></span> <span data-ttu-id="bbd68-117">Další informace najdete v tématu [identity fondu aplikací](/iis/manage/configuring-security/application-pool-identities).</span><span class="sxs-lookup"><span data-stu-id="bbd68-117">For more information, see [Application Pool Identities](/iis/manage/configuring-security/application-pool-identities).</span></span>

## <a name="examples"></a><span data-ttu-id="bbd68-118">Příklady</span><span class="sxs-lookup"><span data-stu-id="bbd68-118">Examples</span></span>

<span data-ttu-id="bbd68-119">Při přístupu k certifikátu, pro který proces nemá oprávnění ke čtení, se zobrazí zpráva o výjimce, která je podobná následujícímu příkladu:</span><span class="sxs-lookup"><span data-stu-id="bbd68-119">When accessing a certificate for which the process doesn't have read privilege, you see an exception message similar to the following example:</span></span>

```output
System.ArgumentException was unhandled
Message="The certificate 'CN=localhost' must have a private key that is capable of key exchange.  The process must have access rights for the private key."
Source="System.ServiceModel"
```

<span data-ttu-id="bbd68-120">V takovém případě použijte nástroj FindPrivateKey k vyhledání souboru privátního klíče a pak nastavte přístupová práva pro proces, pod kterým je služba spuštěná.</span><span class="sxs-lookup"><span data-stu-id="bbd68-120">When this occurs, use the FindPrivateKey tool to find the private key file, and then set the access right for the process that the service is running under.</span></span> <span data-ttu-id="bbd68-121">To lze provést například pomocí nástroje Cacls. exe, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="bbd68-121">For example, this can be done with the Cacls.exe tool as shown in the following example:</span></span>

```console
cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R
```

#### <a name="to-build-the-findprivatekey-project"></a><span data-ttu-id="bbd68-122">Sestavení projektu FindPrivateKey</span><span class="sxs-lookup"><span data-stu-id="bbd68-122">To build the FindPrivateKey project</span></span>

<span data-ttu-id="bbd68-123">Pokud si chcete stáhnout projekt, přejděte na [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459).</span><span class="sxs-lookup"><span data-stu-id="bbd68-123">To download the project, visit [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459).</span></span>

1. <span data-ttu-id="bbd68-124">Otevřete Průzkumníka souborů a přejděte do složky *WF_WCF_Samples \wcf\setup\findprivatekey\cs* v umístění adresáře, kam jste nainstalovali ukázku.</span><span class="sxs-lookup"><span data-stu-id="bbd68-124">Open File Explorer and navigate to the *WF_WCF_Samples\WCF\Setup\FindPrivateKey\CS* folder under the directory location where you installed the sample.</span></span>

2. <span data-ttu-id="bbd68-125">Dvojím kliknutím na ikonu souboru. sln otevřete soubor v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bbd68-125">Double-click the .sln file icon to open the file in Visual Studio.</span></span>

3. <span data-ttu-id="bbd68-126">V nabídce **sestavení** vyberte znovu **Sestavit řešení**.</span><span class="sxs-lookup"><span data-stu-id="bbd68-126">In the **Build** menu, select **Rebuild Solution**.</span></span>

4. <span data-ttu-id="bbd68-127">Sestavení řešení vygeneruje soubor: FindPrivateKey. exe.</span><span class="sxs-lookup"><span data-stu-id="bbd68-127">Building the solution generates the file: FindPrivateKey.exe.</span></span>

## <a name="conventionscommand-line-entries"></a><span data-ttu-id="bbd68-128">Konvence – položky příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="bbd68-128">Conventions—Command-Line entries</span></span>

 <span data-ttu-id="bbd68-129">"[*možnost*]" představuje volitelnou sadu parametrů.</span><span class="sxs-lookup"><span data-stu-id="bbd68-129">"[*option*]" represents an optional set of parameters.</span></span>

 <span data-ttu-id="bbd68-130">{*Option*} představuje povinnou sadu parametrů.</span><span class="sxs-lookup"><span data-stu-id="bbd68-130">"{*option*}" represents a mandatory set of parameters.</span></span>

 <span data-ttu-id="bbd68-131">"*možnost1* &#124; *možnost2*" představuje volbu mezi sadami možností.</span><span class="sxs-lookup"><span data-stu-id="bbd68-131">"*option1* &#124; *option2*" represents a choice between sets of options.</span></span>

 <span data-ttu-id="bbd68-132">"\<*value*>" představuje hodnotu parametru, která se má zadat.</span><span class="sxs-lookup"><span data-stu-id="bbd68-132">"\<*value*>" represents a parameter value to be entered.</span></span>

## <a name="usage"></a><span data-ttu-id="bbd68-133">Použití</span><span class="sxs-lookup"><span data-stu-id="bbd68-133">Usage</span></span>

```console
FindPrivateKey <storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]
```

<span data-ttu-id="bbd68-134">Kde:</span><span class="sxs-lookup"><span data-stu-id="bbd68-134">Where:</span></span>

| <span data-ttu-id="bbd68-135">Parametr</span><span class="sxs-lookup"><span data-stu-id="bbd68-135">Parameter</span></span>         | <span data-ttu-id="bbd68-136">Popis</span><span class="sxs-lookup"><span data-stu-id="bbd68-136">Description</span></span>                                                                       |
|-----------------|-----------------------------------------------------------------------------------|
| `<subjectName>` | <span data-ttu-id="bbd68-137">Název subjektu certifikátu</span><span class="sxs-lookup"><span data-stu-id="bbd68-137">The subject name of the certificate</span></span>                                               |
| `<thumbprint>`  | <span data-ttu-id="bbd68-138">Kryptografický otisk certifikátu (k jeho zjištění můžete použít nástroj certmgr. exe)</span><span class="sxs-lookup"><span data-stu-id="bbd68-138">The thumbprint of the certificate (You can use the Certmgr.exe tool to find this)</span></span> |
| `-f`            | <span data-ttu-id="bbd68-139">pouze název výstupního souboru</span><span class="sxs-lookup"><span data-stu-id="bbd68-139">output file name only</span></span>                                                             |
| `-d`            | <span data-ttu-id="bbd68-140">pouze výstupní adresář</span><span class="sxs-lookup"><span data-stu-id="bbd68-140">output directory only</span></span>                                                             |
| `-a`            | <span data-ttu-id="bbd68-141">název absolutního souboru výstupu</span><span class="sxs-lookup"><span data-stu-id="bbd68-141">output absolute file name</span></span>                                                         |

<span data-ttu-id="bbd68-142">Pokud nejsou zadány žádné parametry na příkazovém řádku, zobrazí se text nápovědy s těmito informacemi.</span><span class="sxs-lookup"><span data-stu-id="bbd68-142">If no parameters are specified at the command prompt, then help text with this information is displayed.</span></span>

## <a name="examples"></a><span data-ttu-id="bbd68-143">Příklady</span><span class="sxs-lookup"><span data-stu-id="bbd68-143">Examples</span></span>

<span data-ttu-id="bbd68-144">Tento příklad vyhledá název souboru certifikátu s názvem subjektu "CN = localhost" v osobním úložišti aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="bbd68-144">This example finds the filename of the certificate with a subject name of "CN=localhost", in the Personal store of the Current User.</span></span>

```console
FindPrivateKey My CurrentUser -n "CN=localhost"
```

<span data-ttu-id="bbd68-145">Tento příklad najde název souboru certifikátu s názvem subjektu "CN = localhost", v osobním úložišti aktuálního uživatele a výstupem úplné cesty k adresáři.</span><span class="sxs-lookup"><span data-stu-id="bbd68-145">This example finds the filename of the certificate with a subject name of "CN=localhost", in the Personal store of the Current User and output the full directory path.</span></span>

```console
FindPrivateKey My CurrentUser -n "CN=localhost" -a
```

<span data-ttu-id="bbd68-146">Tento příklad najde název souboru certifikátu s kryptografickým otiskem "03 33 98 63 D0 47 E7 48 71 33 62 64 76 5c 4C 9d 42 1d 6b 52", v osobním úložišti místního počítače.</span><span class="sxs-lookup"><span data-stu-id="bbd68-146">This example finds the filename of the certificate with a thumbprint of "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52", in the Personal store of the Local Computer.</span></span>

```console
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52"
```
