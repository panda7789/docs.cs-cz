---
title: 'Postupy: Spustit částečně důvěryhodný kód v izolovaném prostoru'
ms.date: 03/30/2017
helpviewer_keywords:
- partially trusted code
- sandboxing
- partial trust
- restricted security environment
- code security, sandboxing
ms.assetid: d1ad722b-5b49-4040-bff3-431b94bb8095
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e8b1db291fbaf19ae9086fe1e2b76a475d198e19
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894559"
---
# <a name="how-to-run-partially-trusted-code-in-a-sandbox"></a><span data-ttu-id="7c36a-102">Postupy: Spustit částečně důvěryhodný kód v izolovaném prostoru</span><span class="sxs-lookup"><span data-stu-id="7c36a-102">How to: Run Partially Trusted Code in a Sandbox</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="7c36a-103">Sandboxing je postup spuštění kódu v prostředí s omezeným zabezpečením, které omezuje oprávnění k přístupu udělené kódu.</span><span class="sxs-lookup"><span data-stu-id="7c36a-103">Sandboxing is the practice of running code in a restricted security environment, which limits the access permissions granted to the code.</span></span> <span data-ttu-id="7c36a-104">Pokud máte například spravovanou knihovnu ze zdroje, kterému nedůvěřujete, neměli byste ji spouštět jako plně důvěryhodnou.</span><span class="sxs-lookup"><span data-stu-id="7c36a-104">For example, if you have a managed library from a source you do not completely trust, you should not run it as fully trusted.</span></span> <span data-ttu-id="7c36a-105">Místo toho byste měli umístit kód do izolovaného prostoru (sandbox), který omezí jeho oprávnění na ty, které očekáváte, že <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> bude potřebovat (například oprávnění).</span><span class="sxs-lookup"><span data-stu-id="7c36a-105">Instead, you should place the code in a sandbox that limits its permissions to those that you expect it to need (for example, <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission).</span></span>  
  
 <span data-ttu-id="7c36a-106">K testování kódu, který se bude spouštět v částečně důvěryhodných prostředích, můžete použít také sandboxing.</span><span class="sxs-lookup"><span data-stu-id="7c36a-106">You can also use sandboxing to test code you will be distributing that will run in partially trusted environments.</span></span>  
  
 <span data-ttu-id="7c36a-107"><xref:System.AppDomain> Představuje efektivní způsob poskytování izolovaného prostoru pro spravované aplikace.</span><span class="sxs-lookup"><span data-stu-id="7c36a-107">An <xref:System.AppDomain> is an effective way of providing a sandbox for managed applications.</span></span> <span data-ttu-id="7c36a-108">Aplikační domény používané pro spouštění částečně důvěryhodného kódu mají oprávnění, která definují chráněné prostředky, které jsou k dispozici při spuštění <xref:System.AppDomain>v rámci.</span><span class="sxs-lookup"><span data-stu-id="7c36a-108">Application domains that are used for running partially trusted code have permissions that define the protected resources that are available when running within that <xref:System.AppDomain>.</span></span> <span data-ttu-id="7c36a-109">Kód, který běží uvnitř <xref:System.AppDomain> , je svázán s oprávněními přidruženými <xref:System.AppDomain> k a má povolen přístup pouze k určeným prostředkům.</span><span class="sxs-lookup"><span data-stu-id="7c36a-109">Code that runs inside the <xref:System.AppDomain> is bound by the permissions associated with the <xref:System.AppDomain> and is allowed to access only the specified resources.</span></span> <span data-ttu-id="7c36a-110"><xref:System.AppDomain> Obsahujetaképole,kterésloužíkidentifikacisestavení,kterámajíbýtnačtena<xref:System.Security.Policy.StrongName> jako plně důvěryhodná.</span><span class="sxs-lookup"><span data-stu-id="7c36a-110">The <xref:System.AppDomain> also includes a <xref:System.Security.Policy.StrongName> array that is used to identify assemblies that are to be loaded as fully trusted.</span></span> <span data-ttu-id="7c36a-111">To umožňuje autorovi <xref:System.AppDomain> spustit novou doménu v izolovaném prostoru, která umožňuje plně důvěřovat konkrétním podpůrným sestavením.</span><span class="sxs-lookup"><span data-stu-id="7c36a-111">This enables the creator of an <xref:System.AppDomain> to start a new sandboxed domain that allows specific helper assemblies to be fully trusted.</span></span> <span data-ttu-id="7c36a-112">Další možností pro načítání sestavení jako plně důvěryhodných je umístit je do globální mezipaměti sestavení (GAC). to však načte sestavení jako plně důvěryhodných ve všech doménách aplikace vytvořených v daném počítači.</span><span class="sxs-lookup"><span data-stu-id="7c36a-112">Another option for loading assemblies as fully trusted is to place them in the global assembly cache; however, that will load assemblies as fully trusted in all application domains created on that computer.</span></span> <span data-ttu-id="7c36a-113">Seznam silných názvů podporuje jedno<xref:System.AppDomain> rozhodnutí, které poskytuje přísnější určení.</span><span class="sxs-lookup"><span data-stu-id="7c36a-113">The list of strong names supports a per-<xref:System.AppDomain> decision that provides more restrictive determination.</span></span>  
  
 <span data-ttu-id="7c36a-114">K určení sady oprávnění <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> pro aplikace, které běží v izolovaném prostoru (sandbox), můžete použít přetížení metody.</span><span class="sxs-lookup"><span data-stu-id="7c36a-114">You can use the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> method overload to specify the permission set for applications that run in a sandbox.</span></span> <span data-ttu-id="7c36a-115">Toto přetížení umožňuje určit přesnou úroveň zabezpečení přístupu kódu, kterou chcete.</span><span class="sxs-lookup"><span data-stu-id="7c36a-115">This overload enables you to specify the exact level of code access security you want.</span></span> <span data-ttu-id="7c36a-116">Sestavení, která jsou načtena <xref:System.AppDomain> do rozhraní pomocí tohoto přetížení, mohou mít buď zadanou sadu udělení oprávnění, nebo mohou být plně důvěryhodná.</span><span class="sxs-lookup"><span data-stu-id="7c36a-116">Assemblies that are loaded into an <xref:System.AppDomain> by using this overload can either have the specified grant set only, or can be fully trusted.</span></span> <span data-ttu-id="7c36a-117">Sestavení je uděleno úplný vztah důvěryhodnosti, pokud se nachází v globální mezipaměti sestavení `fullTrustAssemblies` <xref:System.Security.Policy.StrongName>(GAC) nebo je uvedeno v parametru pole (.).</span><span class="sxs-lookup"><span data-stu-id="7c36a-117">The assembly is granted full trust if it is in the global assembly cache or listed in the `fullTrustAssemblies` (the <xref:System.Security.Policy.StrongName>) array parameter.</span></span> <span data-ttu-id="7c36a-118">Do `fullTrustAssemblies` seznamu by měla být přidána pouze sestavení známá jako plně důvěryhodná.</span><span class="sxs-lookup"><span data-stu-id="7c36a-118">Only assemblies known to be fully trusted should be added to the `fullTrustAssemblies` list.</span></span>  
  
 <span data-ttu-id="7c36a-119">Přetížení má následující signaturu:</span><span class="sxs-lookup"><span data-stu-id="7c36a-119">The overload has the following signature:</span></span>  
  
```csharp
AppDomain.CreateDomain( string friendlyName,  
                        Evidence securityInfo,  
                        AppDomainSetup info,  
                        PermissionSet grantSet,  
                        params StrongName[] fullTrustAssemblies);  
```  
  
 <span data-ttu-id="7c36a-120">Parametry pro <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> přetížení metody určují název <xref:System.AppDomain> <xref:System.AppDomain>, <xref:System.AppDomainSetup> legitimace pro objekt, který identifikuje základ aplikace pro izolovaný prostor (sandbox), nastavené oprávnění k použití a silné názvy pro plně důvěryhodná sestavení.</span><span class="sxs-lookup"><span data-stu-id="7c36a-120">The parameters for the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> method overload specify the name of the <xref:System.AppDomain>, the evidence for the <xref:System.AppDomain>, the <xref:System.AppDomainSetup> object that identifies the application base for the sandbox, the permission set to use, and the strong names for fully trusted assemblies.</span></span>  
  
 <span data-ttu-id="7c36a-121">Z bezpečnostních důvodů by základ aplikace zadaný v `info` parametru neměl být základem aplikace pro hostitelskou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="7c36a-121">For security reasons, the application base specified in the `info` parameter should not be the application base for the hosting application.</span></span>  
  
 <span data-ttu-id="7c36a-122">Pro parametr můžete zadat buď sadu oprávnění, kterou jste explicitně vytvořili, nebo standardní sadu oprávnění vytvořenou <xref:System.Security.SecurityManager.GetStandardSandbox%2A> metodou. `grantSet`</span><span class="sxs-lookup"><span data-stu-id="7c36a-122">For the `grantSet` parameter, you can specify either a permission set you have explicitly created, or a standard permission set created by the <xref:System.Security.SecurityManager.GetStandardSandbox%2A> method.</span></span>  
  
 <span data-ttu-id="7c36a-123">Na rozdíl od <xref:System.AppDomain> většiny načtení se nepoužívá legitimace <xref:System.AppDomain> pro ( `securityInfo` která je poskytnuta parametrem) k určení sady udělení pro částečně důvěryhodná sestavení.</span><span class="sxs-lookup"><span data-stu-id="7c36a-123">Unlike most <xref:System.AppDomain> loads, the evidence for the <xref:System.AppDomain> (which is provided by the `securityInfo` parameter) is not used to determine the grant set for the partially trusted assemblies.</span></span> <span data-ttu-id="7c36a-124">Místo toho je nezávisle určena `grantSet` parametrem.</span><span class="sxs-lookup"><span data-stu-id="7c36a-124">Instead, it is independently specified by the `grantSet` parameter.</span></span> <span data-ttu-id="7c36a-125">Legitimace se ale dá použít k jiným účelům, jako je určení oboru izolovaného úložiště.</span><span class="sxs-lookup"><span data-stu-id="7c36a-125">However, the evidence can be used for other purposes such as determining the isolated storage scope.</span></span>  
  
### <a name="to-run-an-application-in-a-sandbox"></a><span data-ttu-id="7c36a-126">Spuštění aplikace v izolovaném prostoru</span><span class="sxs-lookup"><span data-stu-id="7c36a-126">To run an application in a sandbox</span></span>  
  
1. <span data-ttu-id="7c36a-127">Vytvořte sadu oprávnění, která se udělí nedůvěryhodné aplikaci.</span><span class="sxs-lookup"><span data-stu-id="7c36a-127">Create the permission set to be granted to the untrusted application.</span></span> <span data-ttu-id="7c36a-128">Minimální oprávnění, které můžete udělit, <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> je oprávnění.</span><span class="sxs-lookup"><span data-stu-id="7c36a-128">The minimum permission you can grant is <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission.</span></span> <span data-ttu-id="7c36a-129">Můžete také udělit další oprávnění, která považujete za bezpečné pro nedůvěryhodný kód. například <xref:System.Security.Permissions.IsolatedStorageFilePermission>.</span><span class="sxs-lookup"><span data-stu-id="7c36a-129">You can also grant additional permissions you think might be safe for untrusted code; for example, <xref:System.Security.Permissions.IsolatedStorageFilePermission>.</span></span> <span data-ttu-id="7c36a-130">Následující kód vytvoří novou sadu oprávnění pouze <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> s oprávněním.</span><span class="sxs-lookup"><span data-stu-id="7c36a-130">The following code creates a new permission set with only <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission.</span></span>  
  
    ```csharp
    PermissionSet permSet = new PermissionSet(PermissionState.None);  
    permSet.AddPermission(new SecurityPermission(SecurityPermissionFlag.Execution));  
    ```  
  
     <span data-ttu-id="7c36a-131">Alternativně můžete použít existující pojmenovanou sadu oprávnění, jako je například Internet.</span><span class="sxs-lookup"><span data-stu-id="7c36a-131">Alternatively, you can use an existing named permission set, such as Internet.</span></span>  
  
    ```csharp
    Evidence ev = new Evidence();  
    ev.AddHostEvidence(new Zone(SecurityZone.Internet));  
    PermissionSet internetPS = SecurityManager.GetStandardSandbox(ev);  
    ```  
  
     <span data-ttu-id="7c36a-132">Metoda vrátí buď sadu oprávnění, nebo `LocalIntranet` sadu oprávnění v závislosti na zóně v legitimaci. `Internet` <xref:System.Security.SecurityManager.GetStandardSandbox%2A></span><span class="sxs-lookup"><span data-stu-id="7c36a-132">The <xref:System.Security.SecurityManager.GetStandardSandbox%2A> method returns either an `Internet` permission set or a `LocalIntranet` permission set depending on the zone in the evidence.</span></span> <span data-ttu-id="7c36a-133"><xref:System.Security.SecurityManager.GetStandardSandbox%2A>Vytvoří také oprávnění identity pro některé objekty legitimace předané jako odkazy.</span><span class="sxs-lookup"><span data-stu-id="7c36a-133"><xref:System.Security.SecurityManager.GetStandardSandbox%2A> also constructs identity permissions for some of the evidence objects passed as references.</span></span>  
  
2. <span data-ttu-id="7c36a-134">Podepište sestavení, které obsahuje třídu hostování (s názvem `Sandboxer` v tomto příkladu), která volá nedůvěryhodný kód.</span><span class="sxs-lookup"><span data-stu-id="7c36a-134">Sign the assembly that contains the hosting class (named `Sandboxer` in this example) that calls the untrusted code.</span></span> <span data-ttu-id="7c36a-135">Přidejte použité pro podepsání sestavení <xref:System.Security.Policy.StrongName> do pole `fullTrustAssemblies` parametru <xref:System.AppDomain.CreateDomain%2A> volání. <xref:System.Security.Policy.StrongName></span><span class="sxs-lookup"><span data-stu-id="7c36a-135">Add the <xref:System.Security.Policy.StrongName> used to sign the assembly to the <xref:System.Security.Policy.StrongName> array of the `fullTrustAssemblies` parameter of the <xref:System.AppDomain.CreateDomain%2A> call.</span></span> <span data-ttu-id="7c36a-136">Třída hosting musí běžet jako plně důvěryhodná, aby bylo možné spustit kód s částečným vztahem důvěryhodnosti nebo nabízet služby pro aplikaci s částečným vztahem důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="7c36a-136">The hosting class must run as fully trusted to enable the execution of the partial-trust code or to offer services to the partial-trust application.</span></span> <span data-ttu-id="7c36a-137">Tímto způsobem si přečtete <xref:System.Security.Policy.StrongName> sestavení:</span><span class="sxs-lookup"><span data-stu-id="7c36a-137">This is how you read the <xref:System.Security.Policy.StrongName> of an assembly:</span></span>  
  
    ```csharp
    StrongName fullTrustAssembly = typeof(Sandboxer).Assembly.Evidence.GetHostEvidence<StrongName>();  
    ```  
  
     <span data-ttu-id="7c36a-138">.NET Framework sestavení, jako například mscorlib a System. dll, není nutné přidávat do seznamu úplných vztahů důvěryhodnosti, protože jsou načteny jako plně důvěryhodné z globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="7c36a-138">.NET Framework assemblies such as mscorlib and System.dll do not have to be added to the full-trust list because they are loaded as fully trusted from the global assembly cache.</span></span>  
  
3. <span data-ttu-id="7c36a-139">Inicializujte <xref:System.AppDomain.CreateDomain%2A>parametrmetody. <xref:System.AppDomainSetup></span><span class="sxs-lookup"><span data-stu-id="7c36a-139">Initialize the <xref:System.AppDomainSetup> parameter of the <xref:System.AppDomain.CreateDomain%2A> method.</span></span> <span data-ttu-id="7c36a-140">Pomocí tohoto parametru můžete ovládat mnoho nastavení nového <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="7c36a-140">With this parameter, you can control many of the settings of the new <xref:System.AppDomain>.</span></span> <span data-ttu-id="7c36a-141">Vlastnost je důležité nastavení a měla by se lišit <xref:System.AppDomainSetup.ApplicationBase%2A> od vlastnosti pro <xref:System.AppDomain> hostitelskou aplikaci. <xref:System.AppDomainSetup.ApplicationBase%2A></span><span class="sxs-lookup"><span data-stu-id="7c36a-141">The <xref:System.AppDomainSetup.ApplicationBase%2A> property is an important setting, and should be different from the <xref:System.AppDomainSetup.ApplicationBase%2A> property for the <xref:System.AppDomain> of the hosting application.</span></span> <span data-ttu-id="7c36a-142">Pokud jsou <xref:System.AppDomainSetup.ApplicationBase%2A> nastavení stejná, může aplikace s částečnou důvěryhodností načíst hostitelskou aplikaci (jako plně důvěryhodnou) výjimku, kterou definuje, a zneužije ji tak.</span><span class="sxs-lookup"><span data-stu-id="7c36a-142">If the <xref:System.AppDomainSetup.ApplicationBase%2A> settings are the same, the partial-trust application can get the hosting application to load (as fully trusted) an exception it defines, thus exploiting it.</span></span> <span data-ttu-id="7c36a-143">Toto je další důvod, proč se nedoporučuje zachytit (výjimka).</span><span class="sxs-lookup"><span data-stu-id="7c36a-143">This is another reason why a catch (exception) is not recommended.</span></span> <span data-ttu-id="7c36a-144">Nastavení základu aplikace hostitele odlišně od základu aplikace v izolovaném prostoru (sandbox) snižuje riziko zneužití.</span><span class="sxs-lookup"><span data-stu-id="7c36a-144">Setting the application base of the host differently from the application base of the sandboxed application mitigates the risk of exploits.</span></span>  
  
    ```csharp
    AppDomainSetup adSetup = new AppDomainSetup();  
    adSetup.ApplicationBase = Path.GetFullPath(pathToUntrusted);  
    ```  
  
4. <span data-ttu-id="7c36a-145">Zavolejte přetížení <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> metody pro vytvoření domény aplikace pomocí zadaných parametrů.</span><span class="sxs-lookup"><span data-stu-id="7c36a-145">Call the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> method overload to create the application domain using the parameters we have specified.</span></span>  
  
     <span data-ttu-id="7c36a-146">Signatura této metody je:</span><span class="sxs-lookup"><span data-stu-id="7c36a-146">The signature for this method is:</span></span>  
  
    ```csharp
    public static AppDomain CreateDomain(string friendlyName,   
        Evidence securityInfo, AppDomainSetup info, PermissionSet grantSet,   
        params StrongName[] fullTrustAssemblies)  
    ```  
  
     <span data-ttu-id="7c36a-147">Další informace:</span><span class="sxs-lookup"><span data-stu-id="7c36a-147">Additional information:</span></span>  
  
    - <span data-ttu-id="7c36a-148">Toto je jediné přetížení <xref:System.AppDomain.CreateDomain%2A> metody, která <xref:System.Security.PermissionSet> přijímá jako parametr, a tak jediné přetížení, které umožňuje načíst aplikaci v nastavení částečné důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="7c36a-148">This is the only overload of the <xref:System.AppDomain.CreateDomain%2A> method that takes a <xref:System.Security.PermissionSet> as a parameter, and thus the only overload that lets you load an application in a partial-trust setting.</span></span>  
  
    - <span data-ttu-id="7c36a-149">`evidence` Parametr se nepoužívá k výpočtu sady oprávnění, která se používá pro identifikaci jinými funkcemi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7c36a-149">The `evidence` parameter is not used to calculate a permission set; it is used for identification by other features of the .NET Framework.</span></span>  
  
    - <span data-ttu-id="7c36a-150"><xref:System.AppDomainSetup.ApplicationBase%2A> Nastavení vlastnosti `info` parametru je pro toto přetížení povinné.</span><span class="sxs-lookup"><span data-stu-id="7c36a-150">Setting the <xref:System.AppDomainSetup.ApplicationBase%2A> property of the `info` parameter is mandatory for this overload.</span></span>  
  
    - <span data-ttu-id="7c36a-151">Parametr obsahuje klíčové slovo, což znamená, že není nutné vytvořit <xref:System.Security.Policy.StrongName> pole. `params` `fullTrustAssemblies`</span><span class="sxs-lookup"><span data-stu-id="7c36a-151">The `fullTrustAssemblies` parameter has the `params` keyword, which means that it is not necessary to create a <xref:System.Security.Policy.StrongName> array.</span></span> <span data-ttu-id="7c36a-152">Předání 0, 1 nebo více silných názvů jako parametrů je povoleno.</span><span class="sxs-lookup"><span data-stu-id="7c36a-152">Passing 0, 1, or more strong names as parameters is allowed.</span></span>  
  
    - <span data-ttu-id="7c36a-153">Kód pro vytvoření aplikační domény je:</span><span class="sxs-lookup"><span data-stu-id="7c36a-153">The code to create the application domain is:</span></span>  
  
    ```csharp
    AppDomain newDomain = AppDomain.CreateDomain("Sandbox", null, adSetup, permSet, fullTrustAssembly);  
    ```  
  
5. <span data-ttu-id="7c36a-154">Načtěte kód do izolovaného prostoru <xref:System.AppDomain> , který jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="7c36a-154">Load the code into the sandboxing <xref:System.AppDomain> that you created.</span></span> <span data-ttu-id="7c36a-155">To lze provést dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="7c36a-155">This can be done in two ways:</span></span>  
  
    - <span data-ttu-id="7c36a-156"><xref:System.AppDomain.ExecuteAssembly%2A> Zavolejte metodu pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="7c36a-156">Call the <xref:System.AppDomain.ExecuteAssembly%2A> method for the assembly.</span></span>  
  
    - <span data-ttu-id="7c36a-157">Použijte metodu pro vytvoření instance třídy odvozené z <xref:System.MarshalByRefObject> v New <xref:System.AppDomain>. <xref:System.Activator.CreateInstanceFrom%2A></span><span class="sxs-lookup"><span data-stu-id="7c36a-157">Use the <xref:System.Activator.CreateInstanceFrom%2A> method to create an instance of a class derived from <xref:System.MarshalByRefObject> in the new <xref:System.AppDomain>.</span></span>  
  
     <span data-ttu-id="7c36a-158">Druhý způsob je vhodnější, protože usnadňuje předávání parametrů nové <xref:System.AppDomain> instanci.</span><span class="sxs-lookup"><span data-stu-id="7c36a-158">The second method is preferable, because it makes it easier to pass parameters to the new <xref:System.AppDomain> instance.</span></span> <span data-ttu-id="7c36a-159">Tato <xref:System.Activator.CreateInstanceFrom%2A> metoda poskytuje dvě důležité funkce:</span><span class="sxs-lookup"><span data-stu-id="7c36a-159">The <xref:System.Activator.CreateInstanceFrom%2A> method provides two important features:</span></span>  
  
    - <span data-ttu-id="7c36a-160">Můžete použít základ kódu, který odkazuje na umístění, které neobsahuje vaše sestavení.</span><span class="sxs-lookup"><span data-stu-id="7c36a-160">You can use a code base that points to a location that does not contain your assembly.</span></span>  
  
    - <span data-ttu-id="7c36a-161">Vytvoření můžete provést v rámci <xref:System.Security.CodeAccessPermission.Assert%2A> pro úplnou důvěryhodnost (<xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType>), která umožňuje vytvořit instanci kritické třídy.</span><span class="sxs-lookup"><span data-stu-id="7c36a-161">You can do the creation under an <xref:System.Security.CodeAccessPermission.Assert%2A> for full-trust (<xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType>), which enables you to create an instance of a critical class.</span></span> <span data-ttu-id="7c36a-162">(K tomu dojde vždy, když vaše sestavení nemá žádné značky transparentnosti a je načteno jako plně důvěryhodné.) Proto je třeba pečlivě vytvořit pouze kód, kterému důvěřujete pomocí této funkce, a doporučujeme vytvořit pouze instance plně důvěryhodných tříd v nové doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="7c36a-162">(This happens whenever your assembly has no transparency markings and is loaded as fully trusted.) Therefore, you have to be careful to create only code that you trust with this function, and we recommend that you create only instances of fully trusted classes in the new application domain.</span></span>  
  
    ```csharp
    ObjectHandle handle = Activator.CreateInstanceFrom(  
    newDomain, typeof(Sandboxer).Assembly.ManifestModule.FullyQualifiedName,  
           typeof(Sandboxer).FullName );  
    ```  
  
     <span data-ttu-id="7c36a-163">Všimněte si, že aby bylo možné vytvořit instanci třídy v nové doméně, musí třída rozšiřuje <xref:System.MarshalByRefObject> třídu.</span><span class="sxs-lookup"><span data-stu-id="7c36a-163">Note that in order to create an instance of a class in a new domain, the class has to extend the <xref:System.MarshalByRefObject> class</span></span>  
  
    ```csharp
    class Sandboxer:MarshalByRefObject  
    ```  
  
6. <span data-ttu-id="7c36a-164">Rozbalení nové instance domény do odkazu v této doméně.</span><span class="sxs-lookup"><span data-stu-id="7c36a-164">Unwrap the new domain instance into a reference in this domain.</span></span> <span data-ttu-id="7c36a-165">Tento odkaz slouží ke spuštění nedůvěryhodného kódu.</span><span class="sxs-lookup"><span data-stu-id="7c36a-165">This reference is used to execute the untrusted code.</span></span>  
  
    ```csharp
    Sandboxer newDomainInstance = (Sandboxer) handle.Unwrap();  
    ```  
  
7. <span data-ttu-id="7c36a-166">Volejte metodu v instanci `Sandboxer` třídy, kterou jste právě vytvořili. `ExecuteUntrustedCode`</span><span class="sxs-lookup"><span data-stu-id="7c36a-166">Call the `ExecuteUntrustedCode` method in the instance of the `Sandboxer` class you just created.</span></span>  
  
    ```csharp
    newDomainInstance.ExecuteUntrustedCode(untrustedAssembly, untrustedClass, entryPoint, parameters);  
    ```  
  
     <span data-ttu-id="7c36a-167">Toto volání je spuštěno v doméně aplikace v izolovaném prostoru, která má omezená oprávnění.</span><span class="sxs-lookup"><span data-stu-id="7c36a-167">This call is executed in the sandboxed application domain, which has restricted permissions.</span></span>  
  
    ```csharp
    public void ExecuteUntrustedCode(string assemblyName, string typeName, string entryPoint, Object[] parameters)  
    {  
        //Load the MethodInfo for a method in the new assembly. This might be a method you know, or   
        //you can use Assembly.EntryPoint to get to the entry point in an executable.  
        MethodInfo target = Assembly.Load(assemblyName).GetType(typeName).GetMethod(entryPoint);  
        try  
        {  
            // Invoke the method.  
            target.Invoke(null, parameters);  
        }  
        catch (Exception ex)  
        {  
        //When information is obtained from a SecurityException extra information is provided if it is   
        //accessed in full-trust.  
            new PermissionSet(PermissionState.Unrestricted).Assert();  
            Console.WriteLine("SecurityException caught:\n{0}", ex.ToString());  
            CodeAccessPermission.RevertAssert();  
            Console.ReadLine();  
        }  
    }  
    ```  
  
     <span data-ttu-id="7c36a-168"><xref:System.Reflection>slouží k získání popisovače metody v částečně důvěryhodném sestavení.</span><span class="sxs-lookup"><span data-stu-id="7c36a-168"><xref:System.Reflection> is used to get a handle of a method in the partially trusted assembly.</span></span> <span data-ttu-id="7c36a-169">Popisovač lze použít ke spuštění kódu bezpečným způsobem s minimálními oprávněními.</span><span class="sxs-lookup"><span data-stu-id="7c36a-169">The handle can be used to execute code in a safe way with minimum permissions.</span></span>  
  
     <span data-ttu-id="7c36a-170">V předchozím kódu si poznamenejte <xref:System.Security.PermissionSet.Assert%2A> oprávnění pro plné důvěryhodnosti před <xref:System.Security.SecurityException>tiskem.</span><span class="sxs-lookup"><span data-stu-id="7c36a-170">In the previous code, note the <xref:System.Security.PermissionSet.Assert%2A> for the full-trust permission before printing the <xref:System.Security.SecurityException>.</span></span>  
  
    ```csharp
    new PermissionSet(PermissionState.Unrestricted).Assert()  
    ```  
  
     <span data-ttu-id="7c36a-171">Výraz s úplným vztahem důvěryhodnosti se používá k získání rozšířených <xref:System.Security.SecurityException>informací z.</span><span class="sxs-lookup"><span data-stu-id="7c36a-171">The full-trust assert is used to obtain extended information from the <xref:System.Security.SecurityException>.</span></span> <span data-ttu-id="7c36a-172">Bez rozhraní <xref:System.Security.PermissionSet.Assert%2A> <xref:System.Security.SecurityException.ToString%2A> , Metoda<xref:System.Security.SecurityException> zjistí, že v zásobníku je částečně důvěryhodný kód a omezí vrácené informace.</span><span class="sxs-lookup"><span data-stu-id="7c36a-172">Without the <xref:System.Security.PermissionSet.Assert%2A>, the <xref:System.Security.SecurityException.ToString%2A> method of <xref:System.Security.SecurityException> will discover that there is partially trusted code on the stack and will restrict the information returned.</span></span> <span data-ttu-id="7c36a-173">To může způsobit problémy se zabezpečením, pokud by kód částečného vztahu důvěryhodnosti mohl tyto informace přečíst, ale riziko je neuděluje <xref:System.Security.Permissions.UIPermission>.</span><span class="sxs-lookup"><span data-stu-id="7c36a-173">This could cause security issues if the partial-trust code could read that information, but the risk is mitigated by not granting <xref:System.Security.Permissions.UIPermission>.</span></span> <span data-ttu-id="7c36a-174">Kontrolní výraz s úplným vztahem důvěryhodnosti by měl být použit zřídka a pouze v případě, že jste si jisti, že nepovolujete použití kódu s částečným vztahem důvěryhodnosti ke zvýšení na úplný vztah důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="7c36a-174">The full-trust assert should be used sparingly and only when you are sure that you are not allowing partial-trust code to elevate to full trust.</span></span> <span data-ttu-id="7c36a-175">Jako pravidlo Nevolejte kód, který nedůvěřujete ve stejné funkci a poté, co jste volali kontrolní výraz pro úplný vztah důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="7c36a-175">As a rule, do not call code you do not trust in the same function and after you called an assert for full trust.</span></span> <span data-ttu-id="7c36a-176">Je dobrým zvykem, abyste po dokončení používání kontrolního výrazu vždy vrátili.</span><span class="sxs-lookup"><span data-stu-id="7c36a-176">It is good practice to always revert the assert when you have finished using it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c36a-177">Příklad</span><span class="sxs-lookup"><span data-stu-id="7c36a-177">Example</span></span>  
 <span data-ttu-id="7c36a-178">Následující příklad implementuje postup v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="7c36a-178">The following example implements the procedure in the previous section.</span></span> <span data-ttu-id="7c36a-179">V příkladu projekt s názvem `Sandboxer` v řešení sady Visual Studio obsahuje také projekt s názvem `UntrustedCode`, který implementuje třídu `UntrustedClass`.</span><span class="sxs-lookup"><span data-stu-id="7c36a-179">In the example, a project named `Sandboxer` in a Visual Studio solution also contains a project named `UntrustedCode`, which implements the class `UntrustedClass`.</span></span> <span data-ttu-id="7c36a-180">V tomto scénáři se předpokládá, že jste stáhli sestavení knihovny obsahující metodu, která se má `true` vrátit `false` , nebo aby označovala, zda je zadané číslo Fibonacci číslem.</span><span class="sxs-lookup"><span data-stu-id="7c36a-180">This scenario assumes that you have downloaded a library assembly containing a method that is expected to return `true` or `false` to indicate whether the number you provided is a Fibonacci number.</span></span> <span data-ttu-id="7c36a-181">Místo toho se metoda pokusí přečíst soubor z počítače.</span><span class="sxs-lookup"><span data-stu-id="7c36a-181">Instead, the method attempts to read a file from your computer.</span></span> <span data-ttu-id="7c36a-182">Následující příklad ukazuje nedůvěryhodný kód.</span><span class="sxs-lookup"><span data-stu-id="7c36a-182">The following example shows the untrusted code.</span></span>  
  
```csharp
using System;  
using System.IO;  
namespace UntrustedCode  
{  
    public class UntrustedClass  
    {  
        // Pretend to be a method checking if a number is a Fibonacci  
        // but which actually attempts to read a file.  
        public static bool IsFibonacci(int number)  
        {  
           File.ReadAllText("C:\\Temp\\file.txt");  
           return false;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="7c36a-183">Následující příklad ukazuje `Sandboxer` kód aplikace, který spouští nedůvěryhodný kód.</span><span class="sxs-lookup"><span data-stu-id="7c36a-183">The following example shows the `Sandboxer` application code that executes the untrusted code.</span></span>  
  
```csharp
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.IO;  
using System.Security;  
using System.Security.Policy;  
using System.Security.Permissions;  
using System.Reflection;  
using System.Runtime.Remoting;  
  
//The Sandboxer class needs to derive from MarshalByRefObject so that we can create it in another   
// AppDomain and refer to it from the default AppDomain.  
class Sandboxer : MarshalByRefObject  
{  
    const string pathToUntrusted = @"..\..\..\UntrustedCode\bin\Debug";  
    const string untrustedAssembly = "UntrustedCode";  
    const string untrustedClass = "UntrustedCode.UntrustedClass";  
    const string entryPoint = "IsFibonacci";  
    private static Object[] parameters = { 45 };  
    static void Main()  
    {  
        //Setting the AppDomainSetup. It is very important to set the ApplicationBase to a folder   
        //other than the one in which the sandboxer resides.  
        AppDomainSetup adSetup = new AppDomainSetup();  
        adSetup.ApplicationBase = Path.GetFullPath(pathToUntrusted);  
  
        //Setting the permissions for the AppDomain. We give the permission to execute and to   
        //read/discover the location where the untrusted code is loaded.  
        PermissionSet permSet = new PermissionSet(PermissionState.None);  
        permSet.AddPermission(new SecurityPermission(SecurityPermissionFlag.Execution));  
  
        //We want the sandboxer assembly's strong name, so that we can add it to the full trust list.  
        StrongName fullTrustAssembly = typeof(Sandboxer).Assembly.Evidence.GetHostEvidence<StrongName>();  
  
        //Now we have everything we need to create the AppDomain, so let's create it.  
        AppDomain newDomain = AppDomain.CreateDomain("Sandbox", null, adSetup, permSet, fullTrustAssembly);  
  
        //Use CreateInstanceFrom to load an instance of the Sandboxer class into the  
        //new AppDomain.   
        ObjectHandle handle = Activator.CreateInstanceFrom(  
            newDomain, typeof(Sandboxer).Assembly.ManifestModule.FullyQualifiedName,  
            typeof(Sandboxer).FullName  
            );  
        //Unwrap the new domain instance into a reference in this domain and use it to execute the   
        //untrusted code.  
        Sandboxer newDomainInstance = (Sandboxer) handle.Unwrap();  
        newDomainInstance.ExecuteUntrustedCode(untrustedAssembly, untrustedClass, entryPoint, parameters);  
    }  
    public void ExecuteUntrustedCode(string assemblyName, string typeName, string entryPoint, Object[] parameters)  
    {  
        //Load the MethodInfo for a method in the new Assembly. This might be a method you know, or   
        //you can use Assembly.EntryPoint to get to the main function in an executable.  
        MethodInfo target = Assembly.Load(assemblyName).GetType(typeName).GetMethod(entryPoint);  
        try  
        {  
            //Now invoke the method.  
            bool retVal = (bool)target.Invoke(null, parameters);  
        }  
        catch (Exception ex)  
        {  
            // When we print informations from a SecurityException extra information can be printed if we are   
            //calling it with a full-trust stack.  
            new PermissionSet(PermissionState.Unrestricted).Assert();  
            Console.WriteLine("SecurityException caught:\n{0}", ex.ToString());  
            CodeAccessPermission.RevertAssert();  
            Console.ReadLine();  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="7c36a-184">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7c36a-184">See also</span></span>

- [<span data-ttu-id="7c36a-185">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="7c36a-185">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
