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
ms.openlocfilehash: 05ab0874c980d9e6138ae2bfd720c6d89628613c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33393270"
---
# <a name="how-to-run-partially-trusted-code-in-a-sandbox"></a><span data-ttu-id="9f807-102">Postupy: Spuštění částečně důvěryhodného kódu v izolovaném prostoru</span><span class="sxs-lookup"><span data-stu-id="9f807-102">How to: Run Partially Trusted Code in a Sandbox</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="9f807-103">Sandboxing je postup spuštění kódu v prostředí s omezeným přístupem, což omezí přístup oprávnění udělená kód.</span><span class="sxs-lookup"><span data-stu-id="9f807-103">Sandboxing is the practice of running code in a restricted security environment, which limits the access permissions granted to the code.</span></span> <span data-ttu-id="9f807-104">Například pokud máte spravovanou knihovnu ze zdroje, kterému nedůvěřujete úplně, nespouštějte ji jako plně důvěryhodná.</span><span class="sxs-lookup"><span data-stu-id="9f807-104">For example, if you have a managed library from a source you do not completely trust, you should not run it as fully trusted.</span></span> <span data-ttu-id="9f807-105">Místo toho byste měli umístit kód do izolovaného prostoru, který omezuje její oprávnění na ty, které očekáváte potřebovat (například <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> oprávnění).</span><span class="sxs-lookup"><span data-stu-id="9f807-105">Instead, you should place the code in a sandbox that limits its permissions to those that you expect it to need (for example, <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission).</span></span>  
  
 <span data-ttu-id="9f807-106">Sandboxing můžete také použít k testování kódu, které budete distribuovat, který se spustí v prostředí částečně důvěryhodné.</span><span class="sxs-lookup"><span data-stu-id="9f807-106">You can also use sandboxing to test code you will be distributing that will run in partially trusted environments.</span></span>  
  
 <span data-ttu-id="9f807-107"><xref:System.AppDomain> Je účinný způsob poskytování izolovaném prostoru pro spravované aplikace.</span><span class="sxs-lookup"><span data-stu-id="9f807-107">An <xref:System.AppDomain> is an effective way of providing a sandbox for managed applications.</span></span> <span data-ttu-id="9f807-108">Aplikační domény, které se používají pro spuštění částečně důvěryhodného kódu mají oprávnění definující k chráněným prostředkům, které jsou k dispozici při spuštění v rámci které <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="9f807-108">Application domains that are used for running partially trusted code have permissions that define the protected resources that are available when running within that <xref:System.AppDomain>.</span></span> <span data-ttu-id="9f807-109">Kód, který běží v rámci <xref:System.AppDomain> je svázaná s oprávnění spojená s <xref:System.AppDomain> a je povolen přístup pouze zadané prostředky.</span><span class="sxs-lookup"><span data-stu-id="9f807-109">Code that runs inside the <xref:System.AppDomain> is bound by the permissions associated with the <xref:System.AppDomain> and is allowed to access only the specified resources.</span></span> <span data-ttu-id="9f807-110"><xref:System.AppDomain> Také zahrnuje <xref:System.Security.Policy.StrongName> pole, které se používá k identifikaci sestavení, které mají být načteny jako plně důvěryhodná.</span><span class="sxs-lookup"><span data-stu-id="9f807-110">The <xref:System.AppDomain> also includes a <xref:System.Security.Policy.StrongName> array that is used to identify assemblies that are to be loaded as fully trusted.</span></span> <span data-ttu-id="9f807-111">To umožňuje Tvůrce <xref:System.AppDomain> spustit novou doménu v izolovaném prostoru, která umožňuje konkrétní podpůrné sestavení být plně důvěryhodné.</span><span class="sxs-lookup"><span data-stu-id="9f807-111">This enables the creator of an <xref:System.AppDomain> to start a new sandboxed domain that allows specific helper assemblies to be fully trusted.</span></span> <span data-ttu-id="9f807-112">Další možností pro načtení sestavení jako plně důvěryhodné je umístit do globální mezipaměti sestavení; ale, který načte sestavení jako plně důvěryhodný ve všech doménách aplikací vytvořených v tomto počítači.</span><span class="sxs-lookup"><span data-stu-id="9f807-112">Another option for loading assemblies as fully trusted is to place them in the global assembly cache; however, that will load assemblies as fully trusted in all application domains created on that computer.</span></span> <span data-ttu-id="9f807-113">Seznam silných názvů podporujících za-<xref:System.AppDomain> rozhodnutí, která poskytuje více omezující stanovení.</span><span class="sxs-lookup"><span data-stu-id="9f807-113">The list of strong names supports a per-<xref:System.AppDomain> decision that provides more restrictive determination.</span></span>  
  
 <span data-ttu-id="9f807-114">Můžete použít <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> přetížení metody k zadání oprávnění nastavená pro aplikace, které běží v izolovaném prostoru.</span><span class="sxs-lookup"><span data-stu-id="9f807-114">You can use the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> method overload to specify the permission set for applications that run in a sandbox.</span></span> <span data-ttu-id="9f807-115">Toto přetížení umožňuje určit přesnou úroveň zabezpečení přístupu kódu, které chcete.</span><span class="sxs-lookup"><span data-stu-id="9f807-115">This overload enables you to specify the exact level of code access security you want.</span></span> <span data-ttu-id="9f807-116">Sestavení, která jsou načtena do <xref:System.AppDomain> pomocí tohoto přetížení, mohou mít buď zadaný udělit pouze nastavena, nebo může být plně důvěryhodná.</span><span class="sxs-lookup"><span data-stu-id="9f807-116">Assemblies that are loaded into an <xref:System.AppDomain> by using this overload can either have the specified grant set only, or can be fully trusted.</span></span> <span data-ttu-id="9f807-117">Sestavení jsou udělena úplný vztah důvěryhodnosti, pokud je v globální mezipaměti sestavení nebo uvedené v `fullTrustAssemblies` ( <xref:System.Security.Policy.StrongName>) parametr pole.</span><span class="sxs-lookup"><span data-stu-id="9f807-117">The assembly is granted full trust if it is in the global assembly cache or listed in the `fullTrustAssemblies` (the <xref:System.Security.Policy.StrongName>) array parameter.</span></span> <span data-ttu-id="9f807-118">Pouze sestavení, které jsou známé jako plně důvěryhodný pro by měla být přidány do `fullTrustAssemblies` seznamu.</span><span class="sxs-lookup"><span data-stu-id="9f807-118">Only assemblies known to be fully trusted should be added to the `fullTrustAssemblies` list.</span></span>  
  
 <span data-ttu-id="9f807-119">Přetížení má následující podpis:</span><span class="sxs-lookup"><span data-stu-id="9f807-119">The overload has the following signature:</span></span>  
  
```  
AppDomain.CreateDomain( string friendlyName,  
                        Evidence securityInfo,  
                        AppDomainSetup info,  
                        PermissionSet grantSet,  
                        params StrongName[] fullTrustAssemblies);  
```  
  
 <span data-ttu-id="9f807-120">Parametry <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> přetížení metody zadejte název <xref:System.AppDomain>, důkaz pro <xref:System.AppDomain>, <xref:System.AppDomainSetup> objekt, který identifikuje základní aplikace pro izolovaný prostor, používat sadu oprávnění a silné názvy pro plně důvěryhodný pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="9f807-120">The parameters for the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> method overload specify the name of the <xref:System.AppDomain>, the evidence for the <xref:System.AppDomain>, the <xref:System.AppDomainSetup> object that identifies the application base for the sandbox, the permission set to use, and the strong names for fully trusted assemblies.</span></span>  
  
 <span data-ttu-id="9f807-121">Z bezpečnostních důvodů základní aplikace zadané v `info` parametr nesmí být základ aplikace pro hostitelskou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="9f807-121">For security reasons, the application base specified in the `info` parameter should not be the application base for the hosting application.</span></span>  
  
 <span data-ttu-id="9f807-122">Pro `grantSet` parametr, můžete zadat sadu oprávnění, kterou jste vytvořili explicitně nebo standardní oprávnění, vytvořená <xref:System.Security.SecurityManager.GetStandardSandbox%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="9f807-122">For the `grantSet` parameter, you can specify either a permission set you have explicitly created, or a standard permission set created by the <xref:System.Security.SecurityManager.GetStandardSandbox%2A> method.</span></span>  
  
 <span data-ttu-id="9f807-123">Na rozdíl od většiny <xref:System.AppDomain> načte, důkaz pro <xref:System.AppDomain> (poskytnutá `securityInfo` parametr) neslouží k určení grant nastavit pro částečně důvěryhodné sestavení.</span><span class="sxs-lookup"><span data-stu-id="9f807-123">Unlike most <xref:System.AppDomain> loads, the evidence for the <xref:System.AppDomain> (which is provided by the `securityInfo` parameter) is not used to determine the grant set for the partially trusted assemblies.</span></span> <span data-ttu-id="9f807-124">Místo toho je nezávisle určena podle `grantSet` parametr.</span><span class="sxs-lookup"><span data-stu-id="9f807-124">Instead, it is independently specified by the `grantSet` parameter.</span></span> <span data-ttu-id="9f807-125">Důkaz však lze použít k jiným účelům, jako je například určení rozsahu izolovaného úložiště.</span><span class="sxs-lookup"><span data-stu-id="9f807-125">However, the evidence can be used for other purposes such as determining the isolated storage scope.</span></span>  
  
### <a name="to-run-an-application-in-a-sandbox"></a><span data-ttu-id="9f807-126">Spuštění aplikace v izolovaném prostoru</span><span class="sxs-lookup"><span data-stu-id="9f807-126">To run an application in a sandbox</span></span>  
  
1.  <span data-ttu-id="9f807-127">Vytvořte sadu udělit oprávnění k nedůvěryhodné aplikaci oprávnění.</span><span class="sxs-lookup"><span data-stu-id="9f807-127">Create the permission set to be granted to the untrusted application.</span></span> <span data-ttu-id="9f807-128">Minimální oprávnění můžete udělit je <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> oprávnění.</span><span class="sxs-lookup"><span data-stu-id="9f807-128">The minimum permission you can grant is <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission.</span></span> <span data-ttu-id="9f807-129">Můžete také udělit další oprávnění, které se domníváte, že může být bezpečné pro přístup z nedůvěryhodné kódu; například <xref:System.Security.Permissions.IsolatedStorageFilePermission>.</span><span class="sxs-lookup"><span data-stu-id="9f807-129">You can also grant additional permissions you think might be safe for untrusted code; for example, <xref:System.Security.Permissions.IsolatedStorageFilePermission>.</span></span> <span data-ttu-id="9f807-130">Následující kód vytvoří novou sadu s pouze oprávnění <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> oprávnění.</span><span class="sxs-lookup"><span data-stu-id="9f807-130">The following code creates a new permission set with only <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission.</span></span>  
  
    ```  
    PermissionSet permSet = new PermissionSet(PermissionState.None);  
    permSet.AddPermission(new SecurityPermission(SecurityPermissionFlag.Execution));  
    ```  
  
     <span data-ttu-id="9f807-131">Alternativně můžete použít existující sadu s názvem oprávnění, jako je Internet.</span><span class="sxs-lookup"><span data-stu-id="9f807-131">Alternatively, you can use an existing named permission set, such as Internet.</span></span>  
  
    ```  
    Evidence ev = new Evidence();  
    ev.AddHostEvidence(new Zone(SecurityZone.Internet));  
    PermissionSet internetPS = SecurityManager.GetStandardSandbox(ev);  
    ```  
  
     <span data-ttu-id="9f807-132"><xref:System.Security.SecurityManager.GetStandardSandbox%2A> Metoda vrací buď `Internet` sadě oprávnění nebo `LocalIntranet` sady v závislosti na zónu důkazy oprávnění.</span><span class="sxs-lookup"><span data-stu-id="9f807-132">The <xref:System.Security.SecurityManager.GetStandardSandbox%2A> method returns either an `Internet` permission set or a `LocalIntranet` permission set depending on the zone in the evidence.</span></span> <span data-ttu-id="9f807-133"><xref:System.Security.SecurityManager.GetStandardSandbox%2A> také vytvoří oprávnění identity pro některé objekty důkaz předané jako odkazy.</span><span class="sxs-lookup"><span data-stu-id="9f807-133"><xref:System.Security.SecurityManager.GetStandardSandbox%2A> also constructs identity permissions for some of the evidence objects passed as references.</span></span>  
  
2.  <span data-ttu-id="9f807-134">Podepisování sestavení, které obsahuje hostující třídy (s názvem `Sandboxer` v tomto příkladu), který volá kód nedůvěryhodné.</span><span class="sxs-lookup"><span data-stu-id="9f807-134">Sign the assembly that contains the hosting class (named `Sandboxer` in this example) that calls the untrusted code.</span></span> <span data-ttu-id="9f807-135">Přidat <xref:System.Security.Policy.StrongName> použité k podepsání sestavení do <xref:System.Security.Policy.StrongName> pole `fullTrustAssemblies` parametr <xref:System.AppDomain.CreateDomain%2A> volání.</span><span class="sxs-lookup"><span data-stu-id="9f807-135">Add the <xref:System.Security.Policy.StrongName> used to sign the assembly to the <xref:System.Security.Policy.StrongName> array of the `fullTrustAssemblies` parameter of the <xref:System.AppDomain.CreateDomain%2A> call.</span></span> <span data-ttu-id="9f807-136">Hostující třídy musí běžet jako plně důvěryhodná, chcete-li povolit spuštění částečně důvěryhodného kódu nebo nabízí služby do aplikace s částečným vztahem důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="9f807-136">The hosting class must run as fully trusted to enable the execution of the partial-trust code or to offer services to the partial-trust application.</span></span> <span data-ttu-id="9f807-137">Toto je, jak číst <xref:System.Security.Policy.StrongName> sestavení:</span><span class="sxs-lookup"><span data-stu-id="9f807-137">This is how you read the <xref:System.Security.Policy.StrongName> of an assembly:</span></span>  
  
    ```  
    StrongName fullTrustAssembly = typeof(Sandboxer).Assembly.Evidence.GetHostEvidence<StrongName>();  
    ```  
  
     <span data-ttu-id="9f807-138">Sestavení rozhraní .NET framework, jako je například mscorlib a System.dll není nutné přidat do seznamu plné důvěryhodnosti, protože jsou načteny jako plně důvěryhodné z globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="9f807-138">.NET Framework assemblies such as mscorlib and System.dll do not have to be added to the full-trust list because they are loaded as fully trusted from the global assembly cache.</span></span>  
  
3.  <span data-ttu-id="9f807-139">Inicializace <xref:System.AppDomainSetup> parametr <xref:System.AppDomain.CreateDomain%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="9f807-139">Initialize the <xref:System.AppDomainSetup> parameter of the <xref:System.AppDomain.CreateDomain%2A> method.</span></span> <span data-ttu-id="9f807-140">Pomocí tohoto parametru, můžete řídit mnoho nastavení nového <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="9f807-140">With this parameter, you can control many of the settings of the new <xref:System.AppDomain>.</span></span> <span data-ttu-id="9f807-141"><xref:System.AppDomainSetup.ApplicationBase%2A> Vlastnost je důležité nastavení a měl by být odlišný od <xref:System.AppDomainSetup.ApplicationBase%2A> vlastnost <xref:System.AppDomain> hostitelské aplikace.</span><span class="sxs-lookup"><span data-stu-id="9f807-141">The <xref:System.AppDomainSetup.ApplicationBase%2A> property is an important setting, and should be different from the <xref:System.AppDomainSetup.ApplicationBase%2A> property for the <xref:System.AppDomain> of the hosting application.</span></span> <span data-ttu-id="9f807-142">Pokud <xref:System.AppDomainSetup.ApplicationBase%2A> nastavení jsou stejné, částečně důvěryhodné aplikace můžete získat hostitelskou aplikaci k načtení (jako je plně důvěryhodná) výjimku definuje, tedy zneužít.</span><span class="sxs-lookup"><span data-stu-id="9f807-142">If the <xref:System.AppDomainSetup.ApplicationBase%2A> settings are the same, the partial-trust application can get the hosting application to load (as fully trusted) an exception it defines, thus exploiting it.</span></span> <span data-ttu-id="9f807-143">To je další důvod, proč se nedoporučuje catch (výjimek).</span><span class="sxs-lookup"><span data-stu-id="9f807-143">This is another reason why a catch (exception) is not recommended.</span></span> <span data-ttu-id="9f807-144">Nastavení aplikace základní hostitele odlišně od základní aplikace v izolovaném prostoru aplikace snižuje riziko zneužití.</span><span class="sxs-lookup"><span data-stu-id="9f807-144">Setting the application base of the host differently from the application base of the sandboxed application mitigates the risk of exploits.</span></span>  
  
    ```  
    AppDomainSetup adSetup = new AppDomainSetup();  
    adSetup.ApplicationBase = Path.GetFullPath(pathToUntrusted);  
    ```  
  
4.  <span data-ttu-id="9f807-145">Volání <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> přetížení metody pro vytvoření domény aplikace pomocí parametrů jsme určili.</span><span class="sxs-lookup"><span data-stu-id="9f807-145">Call the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> method overload to create the application domain using the parameters we have specified.</span></span>  
  
     <span data-ttu-id="9f807-146">Podpis pro tuto metodu je:</span><span class="sxs-lookup"><span data-stu-id="9f807-146">The signature for this method is:</span></span>  
  
    ```  
    public static AppDomain CreateDomain(string friendlyName,   
        Evidence securityInfo, AppDomainSetup info, PermissionSet grantSet,   
        params StrongName[] fullTrustAssemblies)  
    ```  
  
     <span data-ttu-id="9f807-147">Další informace:</span><span class="sxs-lookup"><span data-stu-id="9f807-147">Additional information:</span></span>  
  
    -   <span data-ttu-id="9f807-148">Toto je pouze přetížení <xref:System.AppDomain.CreateDomain%2A> metody, která přijímá <xref:System.Security.PermissionSet> jako parametr a tedy pouze přetížení, které vám umožní načtení aplikace v nastavení částečným vztahem důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="9f807-148">This is the only overload of the <xref:System.AppDomain.CreateDomain%2A> method that takes a <xref:System.Security.PermissionSet> as a parameter, and thus the only overload that lets you load an application in a partial-trust setting.</span></span>  
  
    -   <span data-ttu-id="9f807-149">`evidence` Parametr se nepoužívá k výpočtu sady oprávnění; slouží k určení dalších funkcí rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9f807-149">The `evidence` parameter is not used to calculate a permission set; it is used for identification by other features of the .NET Framework.</span></span>  
  
    -   <span data-ttu-id="9f807-150">Nastavení <xref:System.AppDomainSetup.ApplicationBase%2A> vlastnost `info` parametr je povinný pro toto přetížení.</span><span class="sxs-lookup"><span data-stu-id="9f807-150">Setting the <xref:System.AppDomainSetup.ApplicationBase%2A> property of the `info` parameter is mandatory for this overload.</span></span>  
  
    -   <span data-ttu-id="9f807-151">`fullTrustAssemblies` Parametr má `params` – klíčové slovo, což znamená, že není potřeba vytvořit <xref:System.Security.Policy.StrongName> pole.</span><span class="sxs-lookup"><span data-stu-id="9f807-151">The `fullTrustAssemblies` parameter has the `params` keyword, which means that it is not necessary to create a <xref:System.Security.Policy.StrongName> array.</span></span> <span data-ttu-id="9f807-152">Je povoleno předávání 0, 1 nebo více silných názvů jako parametry.</span><span class="sxs-lookup"><span data-stu-id="9f807-152">Passing 0, 1, or more strong names as parameters is allowed.</span></span>  
  
    -   <span data-ttu-id="9f807-153">Kód k vytvoření domény aplikace je:</span><span class="sxs-lookup"><span data-stu-id="9f807-153">The code to create the application domain is:</span></span>  
  
    ```  
    AppDomain newDomain = AppDomain.CreateDomain("Sandbox", null, adSetup, permSet, fullTrustAssembly);  
    ```  
  
5.  <span data-ttu-id="9f807-154">Načtěte kód do sandboxing <xref:System.AppDomain> kterou jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="9f807-154">Load the code into the sandboxing <xref:System.AppDomain> that you created.</span></span> <span data-ttu-id="9f807-155">Tento krok můžete provést dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="9f807-155">This can be done in two ways:</span></span>  
  
    -   <span data-ttu-id="9f807-156">Volání <xref:System.AppDomain.ExecuteAssembly%2A> metodu pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="9f807-156">Call the <xref:System.AppDomain.ExecuteAssembly%2A> method for the assembly.</span></span>  
  
    -   <span data-ttu-id="9f807-157">Použití <xref:System.Activator.CreateInstanceFrom%2A> metodu pro vytvoření instance třídy odvozené od <xref:System.MarshalByRefObject> v novém <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="9f807-157">Use the <xref:System.Activator.CreateInstanceFrom%2A> method to create an instance of a class derived from <xref:System.MarshalByRefObject> in the new <xref:System.AppDomain>.</span></span>  
  
     <span data-ttu-id="9f807-158">Druhá metoda je vhodnější, protože umožňuje jednodušší předat parametry do nového <xref:System.AppDomain> instance.</span><span class="sxs-lookup"><span data-stu-id="9f807-158">The second method is preferable, because it makes it easier to pass parameters to the new <xref:System.AppDomain> instance.</span></span> <span data-ttu-id="9f807-159"><xref:System.Activator.CreateInstanceFrom%2A> Metoda obsahuje dvě důležité funkce:</span><span class="sxs-lookup"><span data-stu-id="9f807-159">The <xref:System.Activator.CreateInstanceFrom%2A> method provides two important features:</span></span>  
  
    -   <span data-ttu-id="9f807-160">Můžete použít základu kódu, který odkazuje na umístění, které neobsahuje vaše sestavení.</span><span class="sxs-lookup"><span data-stu-id="9f807-160">You can use a code base that points to a location that does not contain your assembly.</span></span>  
  
    -   <span data-ttu-id="9f807-161">Můžete provést vytvoření v rámci <xref:System.Security.CodeAccessPermission.Assert%2A> pro plné důvěryhodnosti (<xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType>), který umožňuje vytvořit instanci kritické třídy.</span><span class="sxs-lookup"><span data-stu-id="9f807-161">You can do the creation under an <xref:System.Security.CodeAccessPermission.Assert%2A> for full-trust (<xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType>), which enables you to create an instance of a critical class.</span></span> <span data-ttu-id="9f807-162">(K tomu dojde vždy, když vaše sestavení nemá žádné označení transparentnosti a je načteno jako plně důvěryhodná.) Proto musíte vytvořit pouze kód, kterému důvěřujete pomocí této funkce pečlivě, a doporučujeme vytvořit pouze instance tříd plně důvěryhodných v nové doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="9f807-162">(This happens whenever your assembly has no transparency markings and is loaded as fully trusted.) Therefore, you have to be careful to create only code that you trust with this function, and we recommend that you create only instances of fully trusted classes in the new application domain.</span></span>  
  
    ```  
    ObjectHandle handle = Activator.CreateInstanceFrom(  
    newDomain, typeof(Sandboxer).Assembly.ManifestModule.FullyQualifiedName,  
           typeof(Sandboxer).FullName );  
    ```  
  
     <span data-ttu-id="9f807-163">Všimněte si, že k vytvoření instance třídy v nové doméně, třída má rozšíření <xref:System.MarshalByRefObject> – třída</span><span class="sxs-lookup"><span data-stu-id="9f807-163">Note that in order to create an instance of a class in a new domain, the class has to extend the <xref:System.MarshalByRefObject> class</span></span>  
  
    ```  
    class Sandboxer:MarshalByRefObject  
    ```  
  
6.  <span data-ttu-id="9f807-164">Rozbalení novou instanci domény do odkaz v této doméně.</span><span class="sxs-lookup"><span data-stu-id="9f807-164">Unwrap the new domain instance into a reference in this domain.</span></span> <span data-ttu-id="9f807-165">Tento odkaz se používá k provedení nedůvěryhodný kód.</span><span class="sxs-lookup"><span data-stu-id="9f807-165">This reference is used to execute the untrusted code.</span></span>  
  
    ```  
    Sandboxer newDomainInstance = (Sandboxer) handle.Unwrap();  
    ```  
  
7.  <span data-ttu-id="9f807-166">Volání `ExecuteUntrustedCode` metoda v instanci systému `Sandboxer` třídy, kterou jste právě vytvořili.</span><span class="sxs-lookup"><span data-stu-id="9f807-166">Call the `ExecuteUntrustedCode` method in the instance of the `Sandboxer` class you just created.</span></span>  
  
    ```  
    newDomainInstance.ExecuteUntrustedCode(untrustedAssembly, untrustedClass, entryPoint, parameters);  
    ```  
  
     <span data-ttu-id="9f807-167">Toto volání se spustí v doméně aplikace v izolovaném prostoru, který má omezená oprávnění.</span><span class="sxs-lookup"><span data-stu-id="9f807-167">This call is executed in the sandboxed application domain, which has restricted permissions.</span></span>  
  
    ```  
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
                (new PermissionSet(PermissionState.Unrestricted)).Assert();  
                Console.WriteLine("SecurityException caught:\n{0}", ex.ToString());  
    CodeAccessPermission.RevertAssert();  
                Console.ReadLine();  
            }  
        }  
    ```  
  
     <span data-ttu-id="9f807-168"><xref:System.Reflection> slouží k získání popisovače metody v částečně důvěryhodné sestavení.</span><span class="sxs-lookup"><span data-stu-id="9f807-168"><xref:System.Reflection> is used to get a handle of a method in the partially trusted assembly.</span></span> <span data-ttu-id="9f807-169">Popisovač slouží ke spouštění kódu bezpečným způsobem s minimálními oprávněními.</span><span class="sxs-lookup"><span data-stu-id="9f807-169">The handle can be used to execute code in a safe way with minimum permissions.</span></span>  
  
     <span data-ttu-id="9f807-170">V předchozí kód, Upozorňujeme <xref:System.Security.PermissionSet.Assert%2A> plná oprávnění před tiskem <xref:System.Security.SecurityException>.</span><span class="sxs-lookup"><span data-stu-id="9f807-170">In the previous code, note the <xref:System.Security.PermissionSet.Assert%2A> for the full-trust permission before printing the <xref:System.Security.SecurityException>.</span></span>  
  
    ```  
    new PermissionSet(PermissionState.Unrestricted)).Assert()  
    ```  
  
     <span data-ttu-id="9f807-171">Assert plné důvěryhodnosti se používá k získání rozšířených informací z <xref:System.Security.SecurityException>.</span><span class="sxs-lookup"><span data-stu-id="9f807-171">The full-trust assert is used to obtain extended information from the <xref:System.Security.SecurityException>.</span></span> <span data-ttu-id="9f807-172">Bez <xref:System.Security.PermissionSet.Assert%2A>, <xref:System.Security.SecurityException.ToString%2A> metodu <xref:System.Security.SecurityException> zjistí, že je částečně důvěryhodného kódu v zásobníku a omezí vrácené informace.</span><span class="sxs-lookup"><span data-stu-id="9f807-172">Without the <xref:System.Security.PermissionSet.Assert%2A>, the <xref:System.Security.SecurityException.ToString%2A> method of <xref:System.Security.SecurityException> will discover that there is partially trusted code on the stack and will restrict the information returned.</span></span> <span data-ttu-id="9f807-173">To může způsobit problémy se zabezpečením, pokud částečně důvěryhodný kód mohl přečíst informace, ale riziko zmírnit neudělením <xref:System.Security.Permissions.UIPermission>.</span><span class="sxs-lookup"><span data-stu-id="9f807-173">This could cause security issues if the partial-trust code could read that information, but the risk is mitigated by not granting <xref:System.Security.Permissions.UIPermission>.</span></span> <span data-ttu-id="9f807-174">Assert plné důvěryhodnosti měli šetřit a jenom v případě, že jste si jisti, že nejsou povolení částečně důvěryhodný kód ke zvýšení oprávnění na úplný vztah důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="9f807-174">The full-trust assert should be used sparingly and only when you are sure that you are not allowing partial-trust code to elevate to full trust.</span></span> <span data-ttu-id="9f807-175">Platí pravidlo upravit kód, který si nejste jisti, ve stejné funkci a po volání požadavku pro úplný vztah důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="9f807-175">As a rule, do not call code you do not trust in the same function and after you called an assert for full trust.</span></span> <span data-ttu-id="9f807-176">Je dobrým zvykem vždy vrátit assert po dokončení jeho použití.</span><span class="sxs-lookup"><span data-stu-id="9f807-176">It is good practice to always revert the assert when you have finished using it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f807-177">Příklad</span><span class="sxs-lookup"><span data-stu-id="9f807-177">Example</span></span>  
 <span data-ttu-id="9f807-178">Následující příklad implementuje podle postupu v předchozím oddílu.</span><span class="sxs-lookup"><span data-stu-id="9f807-178">The following example implements the procedure in the previous section.</span></span> <span data-ttu-id="9f807-179">V příkladu projekt s názvem `Sandboxer` v sadě Visual Studio řešení obsahuje také projekt s názvem `UntrustedCode`, který implementuje třídu `UntrustedClass`.</span><span class="sxs-lookup"><span data-stu-id="9f807-179">In the example, a project named `Sandboxer` in a Visual Studio solution also contains a project named `UntrustedCode`, which implements the class `UntrustedClass`.</span></span> <span data-ttu-id="9f807-180">Tento scénář předpokládá, že jste si stáhli sestavení knihovny obsahující metodu, která zpět `true` nebo `false` indikující, zda počet jste zadali, je Fibonacciho číslo.</span><span class="sxs-lookup"><span data-stu-id="9f807-180">This scenario assumes that you have downloaded a library assembly containing a method that is expected to return `true` or `false` to indicate whether the number you provided is a Fibonacci number.</span></span> <span data-ttu-id="9f807-181">Místo toho metodu pokusí přečíst soubor z vašeho počítače.</span><span class="sxs-lookup"><span data-stu-id="9f807-181">Instead, the method attempts to read a file from your computer.</span></span> <span data-ttu-id="9f807-182">Následující příklad ukazuje kód nedůvěryhodné.</span><span class="sxs-lookup"><span data-stu-id="9f807-182">The following example shows the untrusted code.</span></span>  
  
```  
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
  
 <span data-ttu-id="9f807-183">Následující příklad ukazuje `Sandboxer` aplikační kód, který provede nedůvěryhodný kód.</span><span class="sxs-lookup"><span data-stu-id="9f807-183">The following example shows the `Sandboxer` application code that executes the untrusted code.</span></span>  
  
```  
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
            (new PermissionSet(PermissionState.Unrestricted)).Assert();  
            Console.WriteLine("SecurityException caught:\n{0}", ex.ToString());  
            CodeAccessPermission.RevertAssert();  
            Console.ReadLine();  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="9f807-184">Viz také</span><span class="sxs-lookup"><span data-stu-id="9f807-184">See Also</span></span>  
 [<span data-ttu-id="9f807-185">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="9f807-185">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
