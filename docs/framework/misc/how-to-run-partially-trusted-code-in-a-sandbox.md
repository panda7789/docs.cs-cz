---
title: 'Postupy: Spuštění částečně důvěryhodného kódu v izolovaném prostoru'
description: Zjistěte, jak spustit částečně důvěryhodný kód v izolovaném prostoru (sandbox) v rozhraní .NET. Třída AppDomain představuje efektivní způsob, jakým jsou spravované aplikace izolovaného prostoru (sandbox).
ms.date: 03/30/2017
helpviewer_keywords:
- partially trusted code
- sandboxing
- partial trust
- restricted security environment
- code security, sandboxing
ms.assetid: d1ad722b-5b49-4040-bff3-431b94bb8095
ms.openlocfilehash: 4f186f1d901b51dd4c61ba6b22197465a41f2c44
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/13/2020
ms.locfileid: "86282031"
---
# <a name="how-to-run-partially-trusted-code-in-a-sandbox"></a><span data-ttu-id="a0f87-104">Postupy: Spuštění částečně důvěryhodného kódu v izolovaném prostoru</span><span class="sxs-lookup"><span data-stu-id="a0f87-104">How to: Run Partially Trusted Code in a Sandbox</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="a0f87-105">Sandboxing je postup spuštění kódu v prostředí s omezeným zabezpečením, které omezuje oprávnění k přístupu udělené kódu.</span><span class="sxs-lookup"><span data-stu-id="a0f87-105">Sandboxing is the practice of running code in a restricted security environment, which limits the access permissions granted to the code.</span></span> <span data-ttu-id="a0f87-106">Pokud máte například spravovanou knihovnu ze zdroje, kterému nedůvěřujete, neměli byste ji spouštět jako plně důvěryhodnou.</span><span class="sxs-lookup"><span data-stu-id="a0f87-106">For example, if you have a managed library from a source you do not completely trust, you should not run it as fully trusted.</span></span> <span data-ttu-id="a0f87-107">Místo toho byste měli umístit kód do izolovaného prostoru (sandbox), který omezí jeho oprávnění na ty, které očekáváte, že bude potřebovat (například <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> oprávnění).</span><span class="sxs-lookup"><span data-stu-id="a0f87-107">Instead, you should place the code in a sandbox that limits its permissions to those that you expect it to need (for example, <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission).</span></span>  
  
 <span data-ttu-id="a0f87-108">K testování kódu, který se bude spouštět v částečně důvěryhodných prostředích, můžete použít také sandboxing.</span><span class="sxs-lookup"><span data-stu-id="a0f87-108">You can also use sandboxing to test code you will be distributing that will run in partially trusted environments.</span></span>  
  
 <span data-ttu-id="a0f87-109"><xref:System.AppDomain>Představuje efektivní způsob poskytování izolovaného prostoru pro spravované aplikace.</span><span class="sxs-lookup"><span data-stu-id="a0f87-109">An <xref:System.AppDomain> is an effective way of providing a sandbox for managed applications.</span></span> <span data-ttu-id="a0f87-110">Aplikační domény používané pro spouštění částečně důvěryhodného kódu mají oprávnění, která definují chráněné prostředky, které jsou k dispozici při spuštění v rámci <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="a0f87-110">Application domains that are used for running partially trusted code have permissions that define the protected resources that are available when running within that <xref:System.AppDomain>.</span></span> <span data-ttu-id="a0f87-111">Kód, který běží uvnitř, <xref:System.AppDomain> je svázán s oprávněními přidruženými k <xref:System.AppDomain> a má povolen přístup pouze k určeným prostředkům.</span><span class="sxs-lookup"><span data-stu-id="a0f87-111">Code that runs inside the <xref:System.AppDomain> is bound by the permissions associated with the <xref:System.AppDomain> and is allowed to access only the specified resources.</span></span> <span data-ttu-id="a0f87-112"><xref:System.AppDomain>Obsahuje také <xref:System.Security.Policy.StrongName> pole, které slouží k identifikaci sestavení, která mají být načtena jako plně důvěryhodná.</span><span class="sxs-lookup"><span data-stu-id="a0f87-112">The <xref:System.AppDomain> also includes a <xref:System.Security.Policy.StrongName> array that is used to identify assemblies that are to be loaded as fully trusted.</span></span> <span data-ttu-id="a0f87-113">To umožňuje autorovi <xref:System.AppDomain> spustit novou doménu v izolovaném prostoru, která umožňuje plně důvěřovat konkrétním podpůrným sestavením.</span><span class="sxs-lookup"><span data-stu-id="a0f87-113">This enables the creator of an <xref:System.AppDomain> to start a new sandboxed domain that allows specific helper assemblies to be fully trusted.</span></span> <span data-ttu-id="a0f87-114">Další možností pro načítání sestavení jako plně důvěryhodných je umístit je do globální mezipaměti sestavení (GAC). to však načte sestavení jako plně důvěryhodných ve všech doménách aplikace vytvořených v daném počítači.</span><span class="sxs-lookup"><span data-stu-id="a0f87-114">Another option for loading assemblies as fully trusted is to place them in the global assembly cache; however, that will load assemblies as fully trusted in all application domains created on that computer.</span></span> <span data-ttu-id="a0f87-115">Seznam silných názvů podporuje jedno <xref:System.AppDomain> rozhodnutí, které poskytuje přísnější určení.</span><span class="sxs-lookup"><span data-stu-id="a0f87-115">The list of strong names supports a per-<xref:System.AppDomain> decision that provides more restrictive determination.</span></span>  
  
 <span data-ttu-id="a0f87-116"><xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType>K určení sady oprávnění pro aplikace, které běží v izolovaném prostoru (sandbox), můžete použít přetížení metody.</span><span class="sxs-lookup"><span data-stu-id="a0f87-116">You can use the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> method overload to specify the permission set for applications that run in a sandbox.</span></span> <span data-ttu-id="a0f87-117">Toto přetížení umožňuje určit přesnou úroveň zabezpečení přístupu kódu, kterou chcete.</span><span class="sxs-lookup"><span data-stu-id="a0f87-117">This overload enables you to specify the exact level of code access security you want.</span></span> <span data-ttu-id="a0f87-118">Sestavení, která jsou načtena do rozhraní <xref:System.AppDomain> pomocí tohoto přetížení, mohou mít buď zadanou sadu udělení oprávnění, nebo mohou být plně důvěryhodná.</span><span class="sxs-lookup"><span data-stu-id="a0f87-118">Assemblies that are loaded into an <xref:System.AppDomain> by using this overload can either have the specified grant set only, or can be fully trusted.</span></span> <span data-ttu-id="a0f87-119">Sestavení je uděleno úplný vztah důvěryhodnosti, pokud se nachází v globální mezipaměti sestavení (GAC) nebo je uvedeno v `fullTrustAssemblies` <xref:System.Security.Policy.StrongName> parametru pole (.).</span><span class="sxs-lookup"><span data-stu-id="a0f87-119">The assembly is granted full trust if it is in the global assembly cache or listed in the `fullTrustAssemblies` (the <xref:System.Security.Policy.StrongName>) array parameter.</span></span> <span data-ttu-id="a0f87-120">Do seznamu by měla být přidána pouze sestavení známá jako plně důvěryhodná `fullTrustAssemblies` .</span><span class="sxs-lookup"><span data-stu-id="a0f87-120">Only assemblies known to be fully trusted should be added to the `fullTrustAssemblies` list.</span></span>  
  
 <span data-ttu-id="a0f87-121">Přetížení má následující signaturu:</span><span class="sxs-lookup"><span data-stu-id="a0f87-121">The overload has the following signature:</span></span>  
  
```csharp
AppDomain.CreateDomain( string friendlyName,  
                        Evidence securityInfo,  
                        AppDomainSetup info,  
                        PermissionSet grantSet,  
                        params StrongName[] fullTrustAssemblies);  
```  
  
 <span data-ttu-id="a0f87-122">Parametry pro <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> přetížení metody určují název <xref:System.AppDomain> , legitimace pro <xref:System.AppDomain> objekt, <xref:System.AppDomainSetup> který identifikuje základ aplikace pro izolovaný prostor (sandbox), sadu oprávnění, která se používá, a silné názvy plně důvěryhodných sestavení.</span><span class="sxs-lookup"><span data-stu-id="a0f87-122">The parameters for the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> method overload specify the name of the <xref:System.AppDomain>, the evidence for the <xref:System.AppDomain>, the <xref:System.AppDomainSetup> object that identifies the application base for the sandbox, the permission set to use, and the strong names for fully trusted assemblies.</span></span>  
  
 <span data-ttu-id="a0f87-123">Z bezpečnostních důvodů by základ aplikace zadaný v parametru neměl `info` být základem aplikace pro hostitelskou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a0f87-123">For security reasons, the application base specified in the `info` parameter should not be the application base for the hosting application.</span></span>  
  
 <span data-ttu-id="a0f87-124">Pro `grantSet` parametr můžete zadat buď sadu oprávnění, kterou jste explicitně vytvořili, nebo standardní sadu oprávnění vytvořenou <xref:System.Security.SecurityManager.GetStandardSandbox%2A> metodou.</span><span class="sxs-lookup"><span data-stu-id="a0f87-124">For the `grantSet` parameter, you can specify either a permission set you have explicitly created, or a standard permission set created by the <xref:System.Security.SecurityManager.GetStandardSandbox%2A> method.</span></span>  
  
 <span data-ttu-id="a0f87-125">Na rozdíl od většiny <xref:System.AppDomain> načtení se nepoužívá legitimace pro <xref:System.AppDomain> (která je poskytnuta `securityInfo` parametrem) k určení sady udělení pro částečně důvěryhodná sestavení.</span><span class="sxs-lookup"><span data-stu-id="a0f87-125">Unlike most <xref:System.AppDomain> loads, the evidence for the <xref:System.AppDomain> (which is provided by the `securityInfo` parameter) is not used to determine the grant set for the partially trusted assemblies.</span></span> <span data-ttu-id="a0f87-126">Místo toho je nezávisle určena `grantSet` parametrem.</span><span class="sxs-lookup"><span data-stu-id="a0f87-126">Instead, it is independently specified by the `grantSet` parameter.</span></span> <span data-ttu-id="a0f87-127">Legitimace se ale dá použít k jiným účelům, jako je určení oboru izolovaného úložiště.</span><span class="sxs-lookup"><span data-stu-id="a0f87-127">However, the evidence can be used for other purposes such as determining the isolated storage scope.</span></span>  
  
### <a name="to-run-an-application-in-a-sandbox"></a><span data-ttu-id="a0f87-128">Spuštění aplikace v izolovaném prostoru</span><span class="sxs-lookup"><span data-stu-id="a0f87-128">To run an application in a sandbox</span></span>  
  
1. <span data-ttu-id="a0f87-129">Vytvořte sadu oprávnění, která se udělí nedůvěryhodné aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a0f87-129">Create the permission set to be granted to the untrusted application.</span></span> <span data-ttu-id="a0f87-130">Minimální oprávnění, které můžete udělit, je <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> oprávnění.</span><span class="sxs-lookup"><span data-stu-id="a0f87-130">The minimum permission you can grant is <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission.</span></span> <span data-ttu-id="a0f87-131">Můžete také udělit další oprávnění, která považujete za bezpečné pro nedůvěryhodný kód. například <xref:System.Security.Permissions.IsolatedStorageFilePermission> .</span><span class="sxs-lookup"><span data-stu-id="a0f87-131">You can also grant additional permissions you think might be safe for untrusted code; for example, <xref:System.Security.Permissions.IsolatedStorageFilePermission>.</span></span> <span data-ttu-id="a0f87-132">Následující kód vytvoří novou sadu oprávnění pouze s <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> oprávněním.</span><span class="sxs-lookup"><span data-stu-id="a0f87-132">The following code creates a new permission set with only <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission.</span></span>  
  
    ```csharp
    PermissionSet permSet = new PermissionSet(PermissionState.None);  
    permSet.AddPermission(new SecurityPermission(SecurityPermissionFlag.Execution));  
    ```  
  
     <span data-ttu-id="a0f87-133">Alternativně můžete použít existující pojmenovanou sadu oprávnění, jako je například Internet.</span><span class="sxs-lookup"><span data-stu-id="a0f87-133">Alternatively, you can use an existing named permission set, such as Internet.</span></span>  
  
    ```csharp
    Evidence ev = new Evidence();  
    ev.AddHostEvidence(new Zone(SecurityZone.Internet));  
    PermissionSet internetPS = SecurityManager.GetStandardSandbox(ev);  
    ```  
  
     <span data-ttu-id="a0f87-134"><xref:System.Security.SecurityManager.GetStandardSandbox%2A>Metoda vrátí buď `Internet` sadu oprávnění, nebo `LocalIntranet` sadu oprávnění v závislosti na zóně v legitimaci.</span><span class="sxs-lookup"><span data-stu-id="a0f87-134">The <xref:System.Security.SecurityManager.GetStandardSandbox%2A> method returns either an `Internet` permission set or a `LocalIntranet` permission set depending on the zone in the evidence.</span></span> <span data-ttu-id="a0f87-135"><xref:System.Security.SecurityManager.GetStandardSandbox%2A>Vytvoří také oprávnění identity pro některé objekty legitimace předané jako odkazy.</span><span class="sxs-lookup"><span data-stu-id="a0f87-135"><xref:System.Security.SecurityManager.GetStandardSandbox%2A> also constructs identity permissions for some of the evidence objects passed as references.</span></span>  
  
2. <span data-ttu-id="a0f87-136">Podepište sestavení, které obsahuje třídu hostování (s názvem `Sandboxer` v tomto příkladu), která volá nedůvěryhodný kód.</span><span class="sxs-lookup"><span data-stu-id="a0f87-136">Sign the assembly that contains the hosting class (named `Sandboxer` in this example) that calls the untrusted code.</span></span> <span data-ttu-id="a0f87-137">Přidejte <xref:System.Security.Policy.StrongName> použité pro podepsání sestavení do <xref:System.Security.Policy.StrongName> pole `fullTrustAssemblies` parametru <xref:System.AppDomain.CreateDomain%2A> volání.</span><span class="sxs-lookup"><span data-stu-id="a0f87-137">Add the <xref:System.Security.Policy.StrongName> used to sign the assembly to the <xref:System.Security.Policy.StrongName> array of the `fullTrustAssemblies` parameter of the <xref:System.AppDomain.CreateDomain%2A> call.</span></span> <span data-ttu-id="a0f87-138">Třída hosting musí běžet jako plně důvěryhodná, aby bylo možné spustit kód s částečným vztahem důvěryhodnosti nebo nabízet služby pro aplikaci s částečným vztahem důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="a0f87-138">The hosting class must run as fully trusted to enable the execution of the partial-trust code or to offer services to the partial-trust application.</span></span> <span data-ttu-id="a0f87-139">Tímto způsobem si přečtete <xref:System.Security.Policy.StrongName> sestavení:</span><span class="sxs-lookup"><span data-stu-id="a0f87-139">This is how you read the <xref:System.Security.Policy.StrongName> of an assembly:</span></span>  
  
    ```csharp
    StrongName fullTrustAssembly = typeof(Sandboxer).Assembly.Evidence.GetHostEvidence<StrongName>();  
    ```  
  
     <span data-ttu-id="a0f87-140">.NET Framework sestavení, jako je například mscorlib a System.dll, není nutné přidávat do seznamu úplných vztahů důvěryhodnosti, protože jsou načteny jako plně důvěryhodné z globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="a0f87-140">.NET Framework assemblies such as mscorlib and System.dll do not have to be added to the full-trust list because they are loaded as fully trusted from the global assembly cache.</span></span>  
  
3. <span data-ttu-id="a0f87-141">Inicializujte <xref:System.AppDomainSetup> parametr <xref:System.AppDomain.CreateDomain%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="a0f87-141">Initialize the <xref:System.AppDomainSetup> parameter of the <xref:System.AppDomain.CreateDomain%2A> method.</span></span> <span data-ttu-id="a0f87-142">Pomocí tohoto parametru můžete ovládat mnoho nastavení nového <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="a0f87-142">With this parameter, you can control many of the settings of the new <xref:System.AppDomain>.</span></span> <span data-ttu-id="a0f87-143"><xref:System.AppDomainSetup.ApplicationBase%2A>Vlastnost je důležité nastavení a měla by se lišit od <xref:System.AppDomainSetup.ApplicationBase%2A> vlastnosti pro <xref:System.AppDomain> hostitelskou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a0f87-143">The <xref:System.AppDomainSetup.ApplicationBase%2A> property is an important setting, and should be different from the <xref:System.AppDomainSetup.ApplicationBase%2A> property for the <xref:System.AppDomain> of the hosting application.</span></span> <span data-ttu-id="a0f87-144">Pokud <xref:System.AppDomainSetup.ApplicationBase%2A> jsou nastavení stejná, může aplikace s částečnou důvěryhodností načíst hostitelskou aplikaci (jako plně důvěryhodnou) výjimku, kterou definuje, a zneužije ji tak.</span><span class="sxs-lookup"><span data-stu-id="a0f87-144">If the <xref:System.AppDomainSetup.ApplicationBase%2A> settings are the same, the partial-trust application can get the hosting application to load (as fully trusted) an exception it defines, thus exploiting it.</span></span> <span data-ttu-id="a0f87-145">Toto je další důvod, proč se nedoporučuje zachytit (výjimka).</span><span class="sxs-lookup"><span data-stu-id="a0f87-145">This is another reason why a catch (exception) is not recommended.</span></span> <span data-ttu-id="a0f87-146">Nastavení základu aplikace hostitele odlišně od základu aplikace v izolovaném prostoru (sandbox) snižuje riziko zneužití.</span><span class="sxs-lookup"><span data-stu-id="a0f87-146">Setting the application base of the host differently from the application base of the sandboxed application mitigates the risk of exploits.</span></span>  
  
    ```csharp
    AppDomainSetup adSetup = new AppDomainSetup();  
    adSetup.ApplicationBase = Path.GetFullPath(pathToUntrusted);  
    ```  
  
4. <span data-ttu-id="a0f87-147">Zavolejte <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> přetížení metody pro vytvoření domény aplikace pomocí zadaných parametrů.</span><span class="sxs-lookup"><span data-stu-id="a0f87-147">Call the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> method overload to create the application domain using the parameters we have specified.</span></span>  
  
     <span data-ttu-id="a0f87-148">Signatura této metody je:</span><span class="sxs-lookup"><span data-stu-id="a0f87-148">The signature for this method is:</span></span>  
  
    ```csharp
    public static AppDomain CreateDomain(string friendlyName,
        Evidence securityInfo, AppDomainSetup info, PermissionSet grantSet,
        params StrongName[] fullTrustAssemblies)  
    ```  
  
     <span data-ttu-id="a0f87-149">Další informace:</span><span class="sxs-lookup"><span data-stu-id="a0f87-149">Additional information:</span></span>  
  
    - <span data-ttu-id="a0f87-150">Toto je jediné přetížení <xref:System.AppDomain.CreateDomain%2A> metody, která přijímá <xref:System.Security.PermissionSet> jako parametr, a tak jediné přetížení, které umožňuje načíst aplikaci v nastavení částečné důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="a0f87-150">This is the only overload of the <xref:System.AppDomain.CreateDomain%2A> method that takes a <xref:System.Security.PermissionSet> as a parameter, and thus the only overload that lets you load an application in a partial-trust setting.</span></span>  
  
    - <span data-ttu-id="a0f87-151">`evidence`Parametr se nepoužívá k výpočtu sady oprávnění, která se používá pro identifikaci jinými funkcemi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a0f87-151">The `evidence` parameter is not used to calculate a permission set; it is used for identification by other features of the .NET Framework.</span></span>  
  
    - <span data-ttu-id="a0f87-152">Nastavení <xref:System.AppDomainSetup.ApplicationBase%2A> vlastnosti `info` parametru je pro toto přetížení povinné.</span><span class="sxs-lookup"><span data-stu-id="a0f87-152">Setting the <xref:System.AppDomainSetup.ApplicationBase%2A> property of the `info` parameter is mandatory for this overload.</span></span>  
  
    - <span data-ttu-id="a0f87-153">`fullTrustAssemblies`Parametr obsahuje `params` klíčové slovo, což znamená, že není nutné vytvořit <xref:System.Security.Policy.StrongName> pole.</span><span class="sxs-lookup"><span data-stu-id="a0f87-153">The `fullTrustAssemblies` parameter has the `params` keyword, which means that it is not necessary to create a <xref:System.Security.Policy.StrongName> array.</span></span> <span data-ttu-id="a0f87-154">Předání 0, 1 nebo více silných názvů jako parametrů je povoleno.</span><span class="sxs-lookup"><span data-stu-id="a0f87-154">Passing 0, 1, or more strong names as parameters is allowed.</span></span>  
  
    - <span data-ttu-id="a0f87-155">Kód pro vytvoření aplikační domény je:</span><span class="sxs-lookup"><span data-stu-id="a0f87-155">The code to create the application domain is:</span></span>  
  
    ```csharp
    AppDomain newDomain = AppDomain.CreateDomain("Sandbox", null, adSetup, permSet, fullTrustAssembly);  
    ```  
  
5. <span data-ttu-id="a0f87-156">Načtěte kód do izolovaného prostoru <xref:System.AppDomain> , který jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="a0f87-156">Load the code into the sandboxing <xref:System.AppDomain> that you created.</span></span> <span data-ttu-id="a0f87-157">To lze provést dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="a0f87-157">This can be done in two ways:</span></span>  
  
    - <span data-ttu-id="a0f87-158">Zavolejte <xref:System.AppDomain.ExecuteAssembly%2A> metodu pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="a0f87-158">Call the <xref:System.AppDomain.ExecuteAssembly%2A> method for the assembly.</span></span>  
  
    - <span data-ttu-id="a0f87-159">Použijte <xref:System.Activator.CreateInstanceFrom%2A> metodu pro vytvoření instance třídy odvozené z <xref:System.MarshalByRefObject> v New <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="a0f87-159">Use the <xref:System.Activator.CreateInstanceFrom%2A> method to create an instance of a class derived from <xref:System.MarshalByRefObject> in the new <xref:System.AppDomain>.</span></span>  
  
     <span data-ttu-id="a0f87-160">Druhý způsob je vhodnější, protože usnadňuje předávání parametrů nové <xref:System.AppDomain> instanci.</span><span class="sxs-lookup"><span data-stu-id="a0f87-160">The second method is preferable, because it makes it easier to pass parameters to the new <xref:System.AppDomain> instance.</span></span> <span data-ttu-id="a0f87-161">Tato <xref:System.Activator.CreateInstanceFrom%2A> Metoda poskytuje dvě důležité funkce:</span><span class="sxs-lookup"><span data-stu-id="a0f87-161">The <xref:System.Activator.CreateInstanceFrom%2A> method provides two important features:</span></span>  
  
    - <span data-ttu-id="a0f87-162">Můžete použít základ kódu, který odkazuje na umístění, které neobsahuje vaše sestavení.</span><span class="sxs-lookup"><span data-stu-id="a0f87-162">You can use a code base that points to a location that does not contain your assembly.</span></span>  
  
    - <span data-ttu-id="a0f87-163">Vytvoření můžete provést v rámci <xref:System.Security.CodeAccessPermission.Assert%2A> pro úplnou důvěryhodnost ( <xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType> ), která umožňuje vytvořit instanci kritické třídy.</span><span class="sxs-lookup"><span data-stu-id="a0f87-163">You can do the creation under an <xref:System.Security.CodeAccessPermission.Assert%2A> for full-trust (<xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType>), which enables you to create an instance of a critical class.</span></span> <span data-ttu-id="a0f87-164">(K tomu dojde vždy, když vaše sestavení nemá žádné značky transparentnosti a je načteno jako plně důvěryhodné.) Proto je třeba pečlivě vytvořit pouze kód, kterému důvěřujete pomocí této funkce, a doporučujeme vytvořit pouze instance plně důvěryhodných tříd v nové doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="a0f87-164">(This happens whenever your assembly has no transparency markings and is loaded as fully trusted.) Therefore, you have to be careful to create only code that you trust with this function, and we recommend that you create only instances of fully trusted classes in the new application domain.</span></span>  
  
    ```csharp
    ObjectHandle handle = Activator.CreateInstanceFrom(  
    newDomain, typeof(Sandboxer).Assembly.ManifestModule.FullyQualifiedName,  
           typeof(Sandboxer).FullName );  
    ```  
  
     <span data-ttu-id="a0f87-165">Všimněte si, že aby bylo možné vytvořit instanci třídy v nové doméně, musí třída rozšiřuje <xref:System.MarshalByRefObject> třídu.</span><span class="sxs-lookup"><span data-stu-id="a0f87-165">Note that in order to create an instance of a class in a new domain, the class has to extend the <xref:System.MarshalByRefObject> class</span></span>  
  
    ```csharp
    class Sandboxer:MarshalByRefObject  
    ```  
  
6. <span data-ttu-id="a0f87-166">Rozbalení nové instance domény do odkazu v této doméně.</span><span class="sxs-lookup"><span data-stu-id="a0f87-166">Unwrap the new domain instance into a reference in this domain.</span></span> <span data-ttu-id="a0f87-167">Tento odkaz slouží ke spuštění nedůvěryhodného kódu.</span><span class="sxs-lookup"><span data-stu-id="a0f87-167">This reference is used to execute the untrusted code.</span></span>  
  
    ```csharp
    Sandboxer newDomainInstance = (Sandboxer) handle.Unwrap();  
    ```  
  
7. <span data-ttu-id="a0f87-168">Volejte `ExecuteUntrustedCode` metodu v instanci `Sandboxer` třídy, kterou jste právě vytvořili.</span><span class="sxs-lookup"><span data-stu-id="a0f87-168">Call the `ExecuteUntrustedCode` method in the instance of the `Sandboxer` class you just created.</span></span>  
  
    ```csharp
    newDomainInstance.ExecuteUntrustedCode(untrustedAssembly, untrustedClass, entryPoint, parameters);  
    ```  
  
     <span data-ttu-id="a0f87-169">Toto volání je spuštěno v doméně aplikace v izolovaném prostoru, která má omezená oprávnění.</span><span class="sxs-lookup"><span data-stu-id="a0f87-169">This call is executed in the sandboxed application domain, which has restricted permissions.</span></span>  
  
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
  
     <span data-ttu-id="a0f87-170"><xref:System.Reflection>slouží k získání popisovače metody v částečně důvěryhodném sestavení.</span><span class="sxs-lookup"><span data-stu-id="a0f87-170"><xref:System.Reflection> is used to get a handle of a method in the partially trusted assembly.</span></span> <span data-ttu-id="a0f87-171">Popisovač lze použít ke spuštění kódu bezpečným způsobem s minimálními oprávněními.</span><span class="sxs-lookup"><span data-stu-id="a0f87-171">The handle can be used to execute code in a safe way with minimum permissions.</span></span>  
  
     <span data-ttu-id="a0f87-172">V předchozím kódu si poznamenejte <xref:System.Security.PermissionSet.Assert%2A> oprávnění pro plné důvěryhodnosti před tiskem <xref:System.Security.SecurityException> .</span><span class="sxs-lookup"><span data-stu-id="a0f87-172">In the previous code, note the <xref:System.Security.PermissionSet.Assert%2A> for the full-trust permission before printing the <xref:System.Security.SecurityException>.</span></span>  
  
    ```csharp
    new PermissionSet(PermissionState.Unrestricted).Assert()  
    ```  
  
     <span data-ttu-id="a0f87-173">Výraz s úplným vztahem důvěryhodnosti se používá k získání rozšířených informací z <xref:System.Security.SecurityException> .</span><span class="sxs-lookup"><span data-stu-id="a0f87-173">The full-trust assert is used to obtain extended information from the <xref:System.Security.SecurityException>.</span></span> <span data-ttu-id="a0f87-174">Bez rozhraní <xref:System.Security.PermissionSet.Assert%2A> , <xref:System.Security.SecurityException.ToString%2A> Metoda zjistí <xref:System.Security.SecurityException> , že v zásobníku je částečně důvěryhodný kód a omezí vrácené informace.</span><span class="sxs-lookup"><span data-stu-id="a0f87-174">Without the <xref:System.Security.PermissionSet.Assert%2A>, the <xref:System.Security.SecurityException.ToString%2A> method of <xref:System.Security.SecurityException> will discover that there is partially trusted code on the stack and will restrict the information returned.</span></span> <span data-ttu-id="a0f87-175">To může způsobit problémy se zabezpečením, pokud by kód částečného vztahu důvěryhodnosti mohl tyto informace přečíst, ale riziko je neuděluje <xref:System.Security.Permissions.UIPermission> .</span><span class="sxs-lookup"><span data-stu-id="a0f87-175">This could cause security issues if the partial-trust code could read that information, but the risk is mitigated by not granting <xref:System.Security.Permissions.UIPermission>.</span></span> <span data-ttu-id="a0f87-176">Kontrolní výraz s úplným vztahem důvěryhodnosti by měl být použit zřídka a pouze v případě, že jste si jisti, že nepovolujete použití kódu s částečným vztahem důvěryhodnosti ke zvýšení na úplný vztah důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="a0f87-176">The full-trust assert should be used sparingly and only when you are sure that you are not allowing partial-trust code to elevate to full trust.</span></span> <span data-ttu-id="a0f87-177">Jako pravidlo Nevolejte kód, který nedůvěřujete ve stejné funkci a poté, co jste volali kontrolní výraz pro úplný vztah důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="a0f87-177">As a rule, do not call code you do not trust in the same function and after you called an assert for full trust.</span></span> <span data-ttu-id="a0f87-178">Je dobrým zvykem, abyste po dokončení používání kontrolního výrazu vždy vrátili.</span><span class="sxs-lookup"><span data-stu-id="a0f87-178">It is good practice to always revert the assert when you have finished using it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0f87-179">Příklad</span><span class="sxs-lookup"><span data-stu-id="a0f87-179">Example</span></span>  
 <span data-ttu-id="a0f87-180">Následující příklad implementuje postup v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="a0f87-180">The following example implements the procedure in the previous section.</span></span> <span data-ttu-id="a0f87-181">V příkladu projekt s názvem `Sandboxer` v řešení sady Visual Studio obsahuje také projekt s názvem `UntrustedCode` , který implementuje třídu `UntrustedClass` .</span><span class="sxs-lookup"><span data-stu-id="a0f87-181">In the example, a project named `Sandboxer` in a Visual Studio solution also contains a project named `UntrustedCode`, which implements the class `UntrustedClass`.</span></span> <span data-ttu-id="a0f87-182">V tomto scénáři se předpokládá, že jste stáhli sestavení knihovny obsahující metodu, která se má vrátit, `true` nebo `false` aby označovala, zda je zadané číslo Fibonacci číslem.</span><span class="sxs-lookup"><span data-stu-id="a0f87-182">This scenario assumes that you have downloaded a library assembly containing a method that is expected to return `true` or `false` to indicate whether the number you provided is a Fibonacci number.</span></span> <span data-ttu-id="a0f87-183">Místo toho se metoda pokusí přečíst soubor z počítače.</span><span class="sxs-lookup"><span data-stu-id="a0f87-183">Instead, the method attempts to read a file from your computer.</span></span> <span data-ttu-id="a0f87-184">Následující příklad ukazuje nedůvěryhodný kód.</span><span class="sxs-lookup"><span data-stu-id="a0f87-184">The following example shows the untrusted code.</span></span>  
  
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
  
 <span data-ttu-id="a0f87-185">Následující příklad ukazuje `Sandboxer` kód aplikace, který spouští nedůvěryhodný kód.</span><span class="sxs-lookup"><span data-stu-id="a0f87-185">The following example shows the `Sandboxer` application code that executes the untrusted code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a0f87-186">Viz také</span><span class="sxs-lookup"><span data-stu-id="a0f87-186">See also</span></span>

- [<span data-ttu-id="a0f87-187">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="a0f87-187">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
