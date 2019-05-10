---
title: 'Postupy: Spuštění částečně důvěryhodného kódu v izolovaném prostoru'
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
ms.openlocfilehash: ff750e6140b1eda8f6537c2f51b9f4769c1d892c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645564"
---
# <a name="how-to-run-partially-trusted-code-in-a-sandbox"></a><span data-ttu-id="5d07f-102">Postupy: Spuštění částečně důvěryhodného kódu v izolovaném prostoru</span><span class="sxs-lookup"><span data-stu-id="5d07f-102">How to: Run Partially Trusted Code in a Sandbox</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="5d07f-103">Izolace (sandbox) je spouštění kódu v prostředí s omezeným přístupem, který omezuje oprávnění udělená kódu.</span><span class="sxs-lookup"><span data-stu-id="5d07f-103">Sandboxing is the practice of running code in a restricted security environment, which limits the access permissions granted to the code.</span></span> <span data-ttu-id="5d07f-104">Například pokud máte spravované knihovny ze zdroje, kterému nedůvěřujete úplně, byste neměli spouštět ji jako plně důvěryhodné.</span><span class="sxs-lookup"><span data-stu-id="5d07f-104">For example, if you have a managed library from a source you do not completely trust, you should not run it as fully trusted.</span></span> <span data-ttu-id="5d07f-105">Místo toho by měl umístit kódu v izolovaném prostoru, který omezuje oprávnění pro ty, které očekáváte, že bude potřebovat (například <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> oprávnění).</span><span class="sxs-lookup"><span data-stu-id="5d07f-105">Instead, you should place the code in a sandbox that limits its permissions to those that you expect it to need (for example, <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission).</span></span>  
  
 <span data-ttu-id="5d07f-106">Izolace (sandbox) můžete také použít k testování kódu, který budete distribuovat, který se spustí v prostředí částečně důvěryhodných.</span><span class="sxs-lookup"><span data-stu-id="5d07f-106">You can also use sandboxing to test code you will be distributing that will run in partially trusted environments.</span></span>  
  
 <span data-ttu-id="5d07f-107"><xref:System.AppDomain> Nabízí efektivní způsob poskytování sandboxu pro spravované aplikace.</span><span class="sxs-lookup"><span data-stu-id="5d07f-107">An <xref:System.AppDomain> is an effective way of providing a sandbox for managed applications.</span></span> <span data-ttu-id="5d07f-108">Aplikační domény, které se používají pro spuštění částečně důvěryhodného kódu mají oprávnění, které definují chráněné prostředky, které jsou k dispozici při spuštění v rámci, která <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="5d07f-108">Application domains that are used for running partially trusted code have permissions that define the protected resources that are available when running within that <xref:System.AppDomain>.</span></span> <span data-ttu-id="5d07f-109">Kód, který běží v rámci <xref:System.AppDomain> oprávnění spojená s vázán <xref:System.AppDomain> a je povolen přístup pouze zadané prostředky.</span><span class="sxs-lookup"><span data-stu-id="5d07f-109">Code that runs inside the <xref:System.AppDomain> is bound by the permissions associated with the <xref:System.AppDomain> and is allowed to access only the specified resources.</span></span> <span data-ttu-id="5d07f-110"><xref:System.AppDomain> Zahrnuje také <xref:System.Security.Policy.StrongName> pole, které slouží k identifikaci sestavení, které mají být načteno jako plně důvěryhodné.</span><span class="sxs-lookup"><span data-stu-id="5d07f-110">The <xref:System.AppDomain> also includes a <xref:System.Security.Policy.StrongName> array that is used to identify assemblies that are to be loaded as fully trusted.</span></span> <span data-ttu-id="5d07f-111">To umožňuje Tvůrce <xref:System.AppDomain> spustit novou doménu v izolovaném prostoru, který umožňuje konkrétní pomocné rutiny sestavení být plně důvěryhodné.</span><span class="sxs-lookup"><span data-stu-id="5d07f-111">This enables the creator of an <xref:System.AppDomain> to start a new sandboxed domain that allows specific helper assemblies to be fully trusted.</span></span> <span data-ttu-id="5d07f-112">Další možností pro načtení sestavení jako plně důvěryhodné je umístit je do globální mezipaměti sestavení; Nicméně, který načte sestavení jako plně důvěryhodný ve všech doménách aplikace vytvořené v tomto počítači.</span><span class="sxs-lookup"><span data-stu-id="5d07f-112">Another option for loading assemblies as fully trusted is to place them in the global assembly cache; however, that will load assemblies as fully trusted in all application domains created on that computer.</span></span> <span data-ttu-id="5d07f-113">Seznam silných názvů podporuje za-<xref:System.AppDomain> rozhodnutí, která poskytuje více omezující rozhodnutí.</span><span class="sxs-lookup"><span data-stu-id="5d07f-113">The list of strong names supports a per-<xref:System.AppDomain> decision that provides more restrictive determination.</span></span>  
  
 <span data-ttu-id="5d07f-114">Můžete použít <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> přetížení metody k určení oprávnění nastavena pro aplikace, které běží v izolovaném prostoru.</span><span class="sxs-lookup"><span data-stu-id="5d07f-114">You can use the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> method overload to specify the permission set for applications that run in a sandbox.</span></span> <span data-ttu-id="5d07f-115">Toto přetížení umožňuje určit přesnou úroveň zabezpečení přístupu kódu, který chcete.</span><span class="sxs-lookup"><span data-stu-id="5d07f-115">This overload enables you to specify the exact level of code access security you want.</span></span> <span data-ttu-id="5d07f-116">Sestavení, která jsou načtena do <xref:System.AppDomain> pomocí tohoto přetížení, mohou mít buď zadaný jenom sada udělení oprávnění, nebo může být plně důvěryhodné.</span><span class="sxs-lookup"><span data-stu-id="5d07f-116">Assemblies that are loaded into an <xref:System.AppDomain> by using this overload can either have the specified grant set only, or can be fully trusted.</span></span> <span data-ttu-id="5d07f-117">Sestavení je udělena úplná důvěryhodnost, pokud se nachází v globální mezipaměti sestavení nebo uvedené v `fullTrustAssemblies` ( <xref:System.Security.Policy.StrongName>) parametr pole.</span><span class="sxs-lookup"><span data-stu-id="5d07f-117">The assembly is granted full trust if it is in the global assembly cache or listed in the `fullTrustAssemblies` (the <xref:System.Security.Policy.StrongName>) array parameter.</span></span> <span data-ttu-id="5d07f-118">Pouze sestavení, které jsou známé jako plně důvěryhodné by měl být přidány do `fullTrustAssemblies` seznamu.</span><span class="sxs-lookup"><span data-stu-id="5d07f-118">Only assemblies known to be fully trusted should be added to the `fullTrustAssemblies` list.</span></span>  
  
 <span data-ttu-id="5d07f-119">Přetížení má následující podpis:</span><span class="sxs-lookup"><span data-stu-id="5d07f-119">The overload has the following signature:</span></span>  
  
```csharp
AppDomain.CreateDomain( string friendlyName,  
                        Evidence securityInfo,  
                        AppDomainSetup info,  
                        PermissionSet grantSet,  
                        params StrongName[] fullTrustAssemblies);  
```  
  
 <span data-ttu-id="5d07f-120">Parametry pro <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> přetížení metody zadejte název <xref:System.AppDomain>, legitimaci <xref:System.AppDomain>, <xref:System.AppDomainSetup> objekt, který identifikuje základní aplikace izolovaného prostoru, oprávnění nastaveno na používání a silných názvů pro plně důvěryhodných sestavení.</span><span class="sxs-lookup"><span data-stu-id="5d07f-120">The parameters for the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> method overload specify the name of the <xref:System.AppDomain>, the evidence for the <xref:System.AppDomain>, the <xref:System.AppDomainSetup> object that identifies the application base for the sandbox, the permission set to use, and the strong names for fully trusted assemblies.</span></span>  
  
 <span data-ttu-id="5d07f-121">Z bezpečnostních důvodů základ cesty aplikace podle `info` parametr nemůže být pro hostitelskou aplikaci základu cesty aplikace.</span><span class="sxs-lookup"><span data-stu-id="5d07f-121">For security reasons, the application base specified in the `info` parameter should not be the application base for the hosting application.</span></span>  
  
 <span data-ttu-id="5d07f-122">Pro `grantSet` parametr, můžete zadat sadu oprávnění, kterou jste vytvořili explicitně nebo standardní oprávnění vytvořená <xref:System.Security.SecurityManager.GetStandardSandbox%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="5d07f-122">For the `grantSet` parameter, you can specify either a permission set you have explicitly created, or a standard permission set created by the <xref:System.Security.SecurityManager.GetStandardSandbox%2A> method.</span></span>  
  
 <span data-ttu-id="5d07f-123">Na rozdíl od většiny <xref:System.AppDomain> důkaz pro načtení <xref:System.AppDomain> (které poskytuje `securityInfo` parametr) se používá k určení udělenou sadu pro částečně důvěryhodná sestavení.</span><span class="sxs-lookup"><span data-stu-id="5d07f-123">Unlike most <xref:System.AppDomain> loads, the evidence for the <xref:System.AppDomain> (which is provided by the `securityInfo` parameter) is not used to determine the grant set for the partially trusted assemblies.</span></span> <span data-ttu-id="5d07f-124">Místo toho je nezávisle určena podle `grantSet` parametru.</span><span class="sxs-lookup"><span data-stu-id="5d07f-124">Instead, it is independently specified by the `grantSet` parameter.</span></span> <span data-ttu-id="5d07f-125">Legitimace však lze použít pro jiné účely, jako je například určování rozsahu izolovaného úložiště.</span><span class="sxs-lookup"><span data-stu-id="5d07f-125">However, the evidence can be used for other purposes such as determining the isolated storage scope.</span></span>  
  
### <a name="to-run-an-application-in-a-sandbox"></a><span data-ttu-id="5d07f-126">Ke spuštění aplikace v izolovaném prostoru</span><span class="sxs-lookup"><span data-stu-id="5d07f-126">To run an application in a sandbox</span></span>  
  
1. <span data-ttu-id="5d07f-127">Vytvořte sadu nedůvěryhodné aplikaci udělit oprávnění.</span><span class="sxs-lookup"><span data-stu-id="5d07f-127">Create the permission set to be granted to the untrusted application.</span></span> <span data-ttu-id="5d07f-128">Je minimální oprávnění může udělit <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> oprávnění.</span><span class="sxs-lookup"><span data-stu-id="5d07f-128">The minimum permission you can grant is <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission.</span></span> <span data-ttu-id="5d07f-129">Můžete také udělit další oprávnění, které si myslíte, že může být bezpečné pro nedůvěryhodný kód; například <xref:System.Security.Permissions.IsolatedStorageFilePermission>.</span><span class="sxs-lookup"><span data-stu-id="5d07f-129">You can also grant additional permissions you think might be safe for untrusted code; for example, <xref:System.Security.Permissions.IsolatedStorageFilePermission>.</span></span> <span data-ttu-id="5d07f-130">Následující kód vytvoří nová sada oprávnění s pouze <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> oprávnění.</span><span class="sxs-lookup"><span data-stu-id="5d07f-130">The following code creates a new permission set with only <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission.</span></span>  
  
    ```csharp
    PermissionSet permSet = new PermissionSet(PermissionState.None);  
    permSet.AddPermission(new SecurityPermission(SecurityPermissionFlag.Execution));  
    ```  
  
     <span data-ttu-id="5d07f-131">Alternativně můžete použít existující sadu pojmenovaných oprávnění, jako je například Internet.</span><span class="sxs-lookup"><span data-stu-id="5d07f-131">Alternatively, you can use an existing named permission set, such as Internet.</span></span>  
  
    ```  
    Evidence ev = new Evidence();  
    ev.AddHostEvidence(new Zone(SecurityZone.Internet));  
    PermissionSet internetPS = SecurityManager.GetStandardSandbox(ev);  
    ```  
  
     <span data-ttu-id="5d07f-132"><xref:System.Security.SecurityManager.GetStandardSandbox%2A> Metoda vrátí buď `Internet` sadu oprávnění nebo `LocalIntranet` sadu v závislosti na zóně legitimace oprávnění.</span><span class="sxs-lookup"><span data-stu-id="5d07f-132">The <xref:System.Security.SecurityManager.GetStandardSandbox%2A> method returns either an `Internet` permission set or a `LocalIntranet` permission set depending on the zone in the evidence.</span></span> <span data-ttu-id="5d07f-133"><xref:System.Security.SecurityManager.GetStandardSandbox%2A> také vytvoří identitu oprávnění pro některé objekty důkazy předané jako odkazy.</span><span class="sxs-lookup"><span data-stu-id="5d07f-133"><xref:System.Security.SecurityManager.GetStandardSandbox%2A> also constructs identity permissions for some of the evidence objects passed as references.</span></span>  
  
2. <span data-ttu-id="5d07f-134">Podepište sestavení obsahující hostující třídy (s názvem `Sandboxer` v tomto příkladu), která volá nedůvěryhodného kódu.</span><span class="sxs-lookup"><span data-stu-id="5d07f-134">Sign the assembly that contains the hosting class (named `Sandboxer` in this example) that calls the untrusted code.</span></span> <span data-ttu-id="5d07f-135">Přidat <xref:System.Security.Policy.StrongName> použitý k podepsání sestavení <xref:System.Security.Policy.StrongName> pole `fullTrustAssemblies` parametr <xref:System.AppDomain.CreateDomain%2A> volání.</span><span class="sxs-lookup"><span data-stu-id="5d07f-135">Add the <xref:System.Security.Policy.StrongName> used to sign the assembly to the <xref:System.Security.Policy.StrongName> array of the `fullTrustAssemblies` parameter of the <xref:System.AppDomain.CreateDomain%2A> call.</span></span> <span data-ttu-id="5d07f-136">Hostující třídy musí běžet jako plně důvěryhodné povolit spuštění částečně důvěryhodného kódu nebo chcete nabízet služby do aplikace částečným vztahem důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="5d07f-136">The hosting class must run as fully trusted to enable the execution of the partial-trust code or to offer services to the partial-trust application.</span></span> <span data-ttu-id="5d07f-137">To je, jak číst <xref:System.Security.Policy.StrongName> sestavení:</span><span class="sxs-lookup"><span data-stu-id="5d07f-137">This is how you read the <xref:System.Security.Policy.StrongName> of an assembly:</span></span>  
  
    ```csharp
    StrongName fullTrustAssembly = typeof(Sandboxer).Assembly.Evidence.GetHostEvidence<StrongName>();  
    ```  
  
     <span data-ttu-id="5d07f-138">Sestavení rozhraní .NET framework, jako je například mscorlib a System.dll, není potřeba přidat do seznamu úplného vztahu důvěryhodnosti, protože pocházejí z globální mezipaměti sestavení načteno jako plně důvěryhodné.</span><span class="sxs-lookup"><span data-stu-id="5d07f-138">.NET Framework assemblies such as mscorlib and System.dll do not have to be added to the full-trust list because they are loaded as fully trusted from the global assembly cache.</span></span>  
  
3. <span data-ttu-id="5d07f-139">Inicializovat <xref:System.AppDomainSetup> parametr <xref:System.AppDomain.CreateDomain%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="5d07f-139">Initialize the <xref:System.AppDomainSetup> parameter of the <xref:System.AppDomain.CreateDomain%2A> method.</span></span> <span data-ttu-id="5d07f-140">S tímto parametrem, můžete řídit celou řadu z nastavení nového <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="5d07f-140">With this parameter, you can control many of the settings of the new <xref:System.AppDomain>.</span></span> <span data-ttu-id="5d07f-141"><xref:System.AppDomainSetup.ApplicationBase%2A> Vlastnost je důležitá nastavení a musí být odlišný od <xref:System.AppDomainSetup.ApplicationBase%2A> vlastnost <xref:System.AppDomain> hostitelské aplikace.</span><span class="sxs-lookup"><span data-stu-id="5d07f-141">The <xref:System.AppDomainSetup.ApplicationBase%2A> property is an important setting, and should be different from the <xref:System.AppDomainSetup.ApplicationBase%2A> property for the <xref:System.AppDomain> of the hosting application.</span></span> <span data-ttu-id="5d07f-142">Pokud <xref:System.AppDomainSetup.ApplicationBase%2A> nastavení jsou stejné, částečným vztahem důvěryhodnosti aplikace můžete získat hostitelskou aplikaci k načtení (jako plně důvěryhodné) definuje, tedy zneužít výjimky.</span><span class="sxs-lookup"><span data-stu-id="5d07f-142">If the <xref:System.AppDomainSetup.ApplicationBase%2A> settings are the same, the partial-trust application can get the hosting application to load (as fully trusted) an exception it defines, thus exploiting it.</span></span> <span data-ttu-id="5d07f-143">To je další důvod, proč se nedoporučuje catch (exception).</span><span class="sxs-lookup"><span data-stu-id="5d07f-143">This is another reason why a catch (exception) is not recommended.</span></span> <span data-ttu-id="5d07f-144">Nastavení aplikace base hostitele odlišně od základ cesty aplikace z aplikace v izolovaném prostoru snižuje riziko zneužití.</span><span class="sxs-lookup"><span data-stu-id="5d07f-144">Setting the application base of the host differently from the application base of the sandboxed application mitigates the risk of exploits.</span></span>  
  
    ```csharp
    AppDomainSetup adSetup = new AppDomainSetup();  
    adSetup.ApplicationBase = Path.GetFullPath(pathToUntrusted);  
    ```  
  
4. <span data-ttu-id="5d07f-145">Volání <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> přetížení metody k vytvoření domény aplikace pomocí parametrů jsme určili.</span><span class="sxs-lookup"><span data-stu-id="5d07f-145">Call the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> method overload to create the application domain using the parameters we have specified.</span></span>  
  
     <span data-ttu-id="5d07f-146">Signatura pro tuto metodu je:</span><span class="sxs-lookup"><span data-stu-id="5d07f-146">The signature for this method is:</span></span>  
  
    ```csharp
    public static AppDomain CreateDomain(string friendlyName,   
        Evidence securityInfo, AppDomainSetup info, PermissionSet grantSet,   
        params StrongName[] fullTrustAssemblies)  
    ```  
  
     <span data-ttu-id="5d07f-147">Další informace:</span><span class="sxs-lookup"><span data-stu-id="5d07f-147">Additional information:</span></span>  
  
    - <span data-ttu-id="5d07f-148">Toto je pouze přetížení <xref:System.AppDomain.CreateDomain%2A> metodu, která přebírá <xref:System.Security.PermissionSet> jako parametr a tedy pouze přetížení, která umožňuje načtení aplikace v částečným vztahem důvěryhodnosti nastavení.</span><span class="sxs-lookup"><span data-stu-id="5d07f-148">This is the only overload of the <xref:System.AppDomain.CreateDomain%2A> method that takes a <xref:System.Security.PermissionSet> as a parameter, and thus the only overload that lets you load an application in a partial-trust setting.</span></span>  
  
    - <span data-ttu-id="5d07f-149">`evidence` Parametr se používá k výpočtu sadu oprávnění, se používá k identifikaci dalších funkcí rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5d07f-149">The `evidence` parameter is not used to calculate a permission set; it is used for identification by other features of the .NET Framework.</span></span>  
  
    - <span data-ttu-id="5d07f-150">Nastavení <xref:System.AppDomainSetup.ApplicationBase%2A> vlastnost `info` parametr je povinný pro toto přetížení.</span><span class="sxs-lookup"><span data-stu-id="5d07f-150">Setting the <xref:System.AppDomainSetup.ApplicationBase%2A> property of the `info` parameter is mandatory for this overload.</span></span>  
  
    - <span data-ttu-id="5d07f-151">`fullTrustAssemblies` Parametr má `params` – klíčové slovo, což znamená, že není nutné vytvořit <xref:System.Security.Policy.StrongName> pole.</span><span class="sxs-lookup"><span data-stu-id="5d07f-151">The `fullTrustAssemblies` parameter has the `params` keyword, which means that it is not necessary to create a <xref:System.Security.Policy.StrongName> array.</span></span> <span data-ttu-id="5d07f-152">Předejte 0, 1 nebo více silných názvů jako parametry je povolen.</span><span class="sxs-lookup"><span data-stu-id="5d07f-152">Passing 0, 1, or more strong names as parameters is allowed.</span></span>  
  
    - <span data-ttu-id="5d07f-153">Kód k vytvoření domény aplikace je:</span><span class="sxs-lookup"><span data-stu-id="5d07f-153">The code to create the application domain is:</span></span>  
  
    ```csharp
    AppDomain newDomain = AppDomain.CreateDomain("Sandbox", null, adSetup, permSet, fullTrustAssembly);  
    ```  
  
5. <span data-ttu-id="5d07f-154">Načíst kód do sandboxing <xref:System.AppDomain> , kterou jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="5d07f-154">Load the code into the sandboxing <xref:System.AppDomain> that you created.</span></span> <span data-ttu-id="5d07f-155">To lze provést dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="5d07f-155">This can be done in two ways:</span></span>  
  
    - <span data-ttu-id="5d07f-156">Volání <xref:System.AppDomain.ExecuteAssembly%2A> metodu pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="5d07f-156">Call the <xref:System.AppDomain.ExecuteAssembly%2A> method for the assembly.</span></span>  
  
    - <span data-ttu-id="5d07f-157">Použití <xref:System.Activator.CreateInstanceFrom%2A> metodu pro vytvoření instance třídy odvozené z <xref:System.MarshalByRefObject> na novém <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="5d07f-157">Use the <xref:System.Activator.CreateInstanceFrom%2A> method to create an instance of a class derived from <xref:System.MarshalByRefObject> in the new <xref:System.AppDomain>.</span></span>  
  
     <span data-ttu-id="5d07f-158">Druhý způsob je vhodnější, protože usnadňuje pro předání parametrů do nového <xref:System.AppDomain> instance.</span><span class="sxs-lookup"><span data-stu-id="5d07f-158">The second method is preferable, because it makes it easier to pass parameters to the new <xref:System.AppDomain> instance.</span></span> <span data-ttu-id="5d07f-159"><xref:System.Activator.CreateInstanceFrom%2A> Metoda obsahuje dvě důležité funkce:</span><span class="sxs-lookup"><span data-stu-id="5d07f-159">The <xref:System.Activator.CreateInstanceFrom%2A> method provides two important features:</span></span>  
  
    - <span data-ttu-id="5d07f-160">Můžete použít, který odkazuje na umístění, které vaše sestavení neobsahuje základ kódu.</span><span class="sxs-lookup"><span data-stu-id="5d07f-160">You can use a code base that points to a location that does not contain your assembly.</span></span>  
  
    - <span data-ttu-id="5d07f-161">Vám pomůžou vytvářet v rámci <xref:System.Security.CodeAccessPermission.Assert%2A> pro plnou důvěryhodnost (<xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType>), což vám umožní vytvořit instanci třídy kritické.</span><span class="sxs-lookup"><span data-stu-id="5d07f-161">You can do the creation under an <xref:System.Security.CodeAccessPermission.Assert%2A> for full-trust (<xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType>), which enables you to create an instance of a critical class.</span></span> <span data-ttu-id="5d07f-162">(Tento proces probíhá vždy sestavení nemá žádné označení transparentnosti a je načteno jako plně důvěryhodné.) Proto budete muset pečlivě vytvořit pouze kód, kterému důvěřujete s touto funkcí a doporučujeme vytvořit pouze instance plně důvěryhodné tříd v nové doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="5d07f-162">(This happens whenever your assembly has no transparency markings and is loaded as fully trusted.) Therefore, you have to be careful to create only code that you trust with this function, and we recommend that you create only instances of fully trusted classes in the new application domain.</span></span>  
  
    ```csharp
    ObjectHandle handle = Activator.CreateInstanceFrom(  
    newDomain, typeof(Sandboxer).Assembly.ManifestModule.FullyQualifiedName,  
           typeof(Sandboxer).FullName );  
    ```  
  
     <span data-ttu-id="5d07f-163">Všimněte si, že k vytvoření instance třídy v nové doméně, třída má rozšířit <xref:System.MarshalByRefObject> třídy</span><span class="sxs-lookup"><span data-stu-id="5d07f-163">Note that in order to create an instance of a class in a new domain, the class has to extend the <xref:System.MarshalByRefObject> class</span></span>  
  
    ```csharp
    class Sandboxer:MarshalByRefObject  
    ```  
  
6. <span data-ttu-id="5d07f-164">Rozbalení novou instanci domény do odkazu v této doméně.</span><span class="sxs-lookup"><span data-stu-id="5d07f-164">Unwrap the new domain instance into a reference in this domain.</span></span> <span data-ttu-id="5d07f-165">Tento odkaz se používá ke spuštění nedůvěryhodného kódu.</span><span class="sxs-lookup"><span data-stu-id="5d07f-165">This reference is used to execute the untrusted code.</span></span>  
  
    ```csharp
    Sandboxer newDomainInstance = (Sandboxer) handle.Unwrap();  
    ```  
  
7. <span data-ttu-id="5d07f-166">Volání `ExecuteUntrustedCode` metoda v instanci aplikace `Sandboxer` třídy, které jste právě vytvořili.</span><span class="sxs-lookup"><span data-stu-id="5d07f-166">Call the `ExecuteUntrustedCode` method in the instance of the `Sandboxer` class you just created.</span></span>  
  
    ```csharp
    newDomainInstance.ExecuteUntrustedCode(untrustedAssembly, untrustedClass, entryPoint, parameters);  
    ```  
  
     <span data-ttu-id="5d07f-167">Toto volání je proveden v doméně aplikace v izolovaném prostoru, který má omezená oprávnění.</span><span class="sxs-lookup"><span data-stu-id="5d07f-167">This call is executed in the sandboxed application domain, which has restricted permissions.</span></span>  
  
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
  
     <span data-ttu-id="5d07f-168"><xref:System.Reflection> slouží k získání popisovače metody v částečně důvěryhodné sestavení.</span><span class="sxs-lookup"><span data-stu-id="5d07f-168"><xref:System.Reflection> is used to get a handle of a method in the partially trusted assembly.</span></span> <span data-ttu-id="5d07f-169">Popisovač lze použít ke spouštění kódu vytvořeného bezpečným způsobem s minimálními oprávněními.</span><span class="sxs-lookup"><span data-stu-id="5d07f-169">The handle can be used to execute code in a safe way with minimum permissions.</span></span>  
  
     <span data-ttu-id="5d07f-170">V předchozím kódu, mějte na paměti <xref:System.Security.PermissionSet.Assert%2A> oprávnění plné důvěryhodnosti před tiskem <xref:System.Security.SecurityException>.</span><span class="sxs-lookup"><span data-stu-id="5d07f-170">In the previous code, note the <xref:System.Security.PermissionSet.Assert%2A> for the full-trust permission before printing the <xref:System.Security.SecurityException>.</span></span>  
  
    ```csharp
    new PermissionSet(PermissionState.Unrestricted).Assert()  
    ```  
  
     <span data-ttu-id="5d07f-171">Kontrolní výraz úplného vztahu důvěryhodnosti se používá k získání rozšířené informace z <xref:System.Security.SecurityException>.</span><span class="sxs-lookup"><span data-stu-id="5d07f-171">The full-trust assert is used to obtain extended information from the <xref:System.Security.SecurityException>.</span></span> <span data-ttu-id="5d07f-172">Bez <xref:System.Security.PermissionSet.Assert%2A>, <xref:System.Security.SecurityException.ToString%2A> metoda <xref:System.Security.SecurityException> zjistí, že je částečně důvěryhodného kódu v zásobníku a omezí vrácené informace.</span><span class="sxs-lookup"><span data-stu-id="5d07f-172">Without the <xref:System.Security.PermissionSet.Assert%2A>, the <xref:System.Security.SecurityException.ToString%2A> method of <xref:System.Security.SecurityException> will discover that there is partially trusted code on the stack and will restrict the information returned.</span></span> <span data-ttu-id="5d07f-173">To může způsobit problémy se zabezpečením, pokud částečně důvěryhodného kódu, které může číst informace, ale riziko zmírnit neudělením <xref:System.Security.Permissions.UIPermission>.</span><span class="sxs-lookup"><span data-stu-id="5d07f-173">This could cause security issues if the partial-trust code could read that information, but the risk is mitigated by not granting <xref:System.Security.Permissions.UIPermission>.</span></span> <span data-ttu-id="5d07f-174">Kontrolní výraz úplného vztahu důvěryhodnosti měly používat střídmě, a pouze v případě, že jste si jisti, že nepovoluje částečně důvěryhodného kódu zvýšit oprávnění na úplný vztah důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="5d07f-174">The full-trust assert should be used sparingly and only when you are sure that you are not allowing partial-trust code to elevate to full trust.</span></span> <span data-ttu-id="5d07f-175">Zpravidla Nevolejte kód, který nedůvěřujete ve stejné funkci a po volání assert pro úplný vztah důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="5d07f-175">As a rule, do not call code you do not trust in the same function and after you called an assert for full trust.</span></span> <span data-ttu-id="5d07f-176">Je vhodné po dokončení jeho použití se vždycky vrátit assert.</span><span class="sxs-lookup"><span data-stu-id="5d07f-176">It is good practice to always revert the assert when you have finished using it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d07f-177">Příklad</span><span class="sxs-lookup"><span data-stu-id="5d07f-177">Example</span></span>  
 <span data-ttu-id="5d07f-178">V následujícím příkladu se implementuje podle postupu v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="5d07f-178">The following example implements the procedure in the previous section.</span></span> <span data-ttu-id="5d07f-179">V tomto příkladu projekt s názvem `Sandboxer` řešení v sadě Visual Studio, také obsahuje projekt s názvem `UntrustedCode`, který implementuje třídu `UntrustedClass`.</span><span class="sxs-lookup"><span data-stu-id="5d07f-179">In the example, a project named `Sandboxer` in a Visual Studio solution also contains a project named `UntrustedCode`, which implements the class `UntrustedClass`.</span></span> <span data-ttu-id="5d07f-180">Tento scénář předpokládá, že jste si stáhli sestavení knihovny obsahující metodu, která se očekává navrácení `true` nebo `false` označující, zda číslo jste zadali, je Fibonacciho číslo.</span><span class="sxs-lookup"><span data-stu-id="5d07f-180">This scenario assumes that you have downloaded a library assembly containing a method that is expected to return `true` or `false` to indicate whether the number you provided is a Fibonacci number.</span></span> <span data-ttu-id="5d07f-181">Místo toho metodu se pokusí přečíst soubor z vašeho počítače.</span><span class="sxs-lookup"><span data-stu-id="5d07f-181">Instead, the method attempts to read a file from your computer.</span></span> <span data-ttu-id="5d07f-182">Následující příklad ukazuje nedůvěryhodný kód.</span><span class="sxs-lookup"><span data-stu-id="5d07f-182">The following example shows the untrusted code.</span></span>  
  
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
  
 <span data-ttu-id="5d07f-183">Následující příklad ukazuje `Sandboxer` aplikační kód, který provede nedůvěryhodný kód.</span><span class="sxs-lookup"><span data-stu-id="5d07f-183">The following example shows the `Sandboxer` application code that executes the untrusted code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5d07f-184">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5d07f-184">See also</span></span>

- [<span data-ttu-id="5d07f-185">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="5d07f-185">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
