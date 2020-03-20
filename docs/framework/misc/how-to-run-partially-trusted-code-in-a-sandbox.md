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
ms.openlocfilehash: b2f5a72e747f6c71743a7b22fe9f1962ac2f6b53
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181182"
---
# <a name="how-to-run-partially-trusted-code-in-a-sandbox"></a><span data-ttu-id="6e472-102">Postupy: Spuštění částečně důvěryhodného kódu v izolovaném prostoru</span><span class="sxs-lookup"><span data-stu-id="6e472-102">How to: Run Partially Trusted Code in a Sandbox</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="6e472-103">Sandboxing je praxe spouštění kódu v prostředí s omezeným zabezpečením, což omezuje přístupová oprávnění udělená kódu.</span><span class="sxs-lookup"><span data-stu-id="6e472-103">Sandboxing is the practice of running code in a restricted security environment, which limits the access permissions granted to the code.</span></span> <span data-ttu-id="6e472-104">Máte-li například spravovanou knihovnu ze zdroje, kterému zcela nedůvěřujete, neměli byste ji spouštět jako plně důvěryhodnou.</span><span class="sxs-lookup"><span data-stu-id="6e472-104">For example, if you have a managed library from a source you do not completely trust, you should not run it as fully trusted.</span></span> <span data-ttu-id="6e472-105">Místo toho byste měli umístit kód do izolovaného prostoru, který omezuje jeho oprávnění <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> na ty, které očekáváte, že bude potřebovat (například oprávnění).</span><span class="sxs-lookup"><span data-stu-id="6e472-105">Instead, you should place the code in a sandbox that limits its permissions to those that you expect it to need (for example, <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission).</span></span>  
  
 <span data-ttu-id="6e472-106">Sandboxing můžete také použít k testování kódu, který budete distribuovat, který bude spuštěn v částečně důvěryhodných prostředích.</span><span class="sxs-lookup"><span data-stu-id="6e472-106">You can also use sandboxing to test code you will be distributing that will run in partially trusted environments.</span></span>  
  
 <span data-ttu-id="6e472-107">A <xref:System.AppDomain> je efektivní způsob, jak poskytnout izolovaného prostoru pro spravované aplikace.</span><span class="sxs-lookup"><span data-stu-id="6e472-107">An <xref:System.AppDomain> is an effective way of providing a sandbox for managed applications.</span></span> <span data-ttu-id="6e472-108">Aplikační domény, které se používají pro spuštění částečně důvěryhodného kódu, mají <xref:System.AppDomain>oprávnění, která definují chráněné prostředky, které jsou k dispozici při spuštění v rámci tohoto .</span><span class="sxs-lookup"><span data-stu-id="6e472-108">Application domains that are used for running partially trusted code have permissions that define the protected resources that are available when running within that <xref:System.AppDomain>.</span></span> <span data-ttu-id="6e472-109">Kód, který <xref:System.AppDomain> běží uvnitř je vázán <xref:System.AppDomain> oprávnění mizená a je povolen přístup pouze k zadaným prostředkům.</span><span class="sxs-lookup"><span data-stu-id="6e472-109">Code that runs inside the <xref:System.AppDomain> is bound by the permissions associated with the <xref:System.AppDomain> and is allowed to access only the specified resources.</span></span> <span data-ttu-id="6e472-110">Obsahuje <xref:System.AppDomain> také <xref:System.Security.Policy.StrongName> pole, které se používá k identifikaci sestavení, které mají být načteny jako plně důvěryhodné.</span><span class="sxs-lookup"><span data-stu-id="6e472-110">The <xref:System.AppDomain> also includes a <xref:System.Security.Policy.StrongName> array that is used to identify assemblies that are to be loaded as fully trusted.</span></span> <span data-ttu-id="6e472-111">To umožňuje <xref:System.AppDomain> autorovi domény s novou sandboxovou součástí, která umožňuje plnou důvěryhodnost konkrétních pomocných sestavení.</span><span class="sxs-lookup"><span data-stu-id="6e472-111">This enables the creator of an <xref:System.AppDomain> to start a new sandboxed domain that allows specific helper assemblies to be fully trusted.</span></span> <span data-ttu-id="6e472-112">Další možností pro načítání sestavení jako plně důvěryhodné je umístit je do globální mezipaměti sestavení; to však načte sestavení jako plně důvěryhodná ve všech aplikačních doménách vytvořených v tomto počítači.</span><span class="sxs-lookup"><span data-stu-id="6e472-112">Another option for loading assemblies as fully trusted is to place them in the global assembly cache; however, that will load assemblies as fully trusted in all application domains created on that computer.</span></span> <span data-ttu-id="6e472-113">Seznam silných názvů podporuje<xref:System.AppDomain> rozhodnutí, které poskytuje restriktivnější určení.</span><span class="sxs-lookup"><span data-stu-id="6e472-113">The list of strong names supports a per-<xref:System.AppDomain> decision that provides more restrictive determination.</span></span>  
  
 <span data-ttu-id="6e472-114">Přetížení <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> metody můžete použít k určení sady oprávnění pro aplikace, které běží v izolovaném prostoru.</span><span class="sxs-lookup"><span data-stu-id="6e472-114">You can use the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> method overload to specify the permission set for applications that run in a sandbox.</span></span> <span data-ttu-id="6e472-115">Toto přetížení umožňuje zadat přesnou úroveň zabezpečení přístupu kódu, které chcete.</span><span class="sxs-lookup"><span data-stu-id="6e472-115">This overload enables you to specify the exact level of code access security you want.</span></span> <span data-ttu-id="6e472-116">Sestavení, které jsou <xref:System.AppDomain> načteny do pomocí tohoto přetížení může mít buď zadanou sadu grantů pouze, nebo může být plně důvěryhodný.</span><span class="sxs-lookup"><span data-stu-id="6e472-116">Assemblies that are loaded into an <xref:System.AppDomain> by using this overload can either have the specified grant set only, or can be fully trusted.</span></span> <span data-ttu-id="6e472-117">Sestavení je udělen úplný vztah důvěryhodnosti, pokud je `fullTrustAssemblies` v <xref:System.Security.Policy.StrongName>globální mezipaměti sestavení nebo je uvedeno v parametru () pole.</span><span class="sxs-lookup"><span data-stu-id="6e472-117">The assembly is granted full trust if it is in the global assembly cache or listed in the `fullTrustAssemblies` (the <xref:System.Security.Policy.StrongName>) array parameter.</span></span> <span data-ttu-id="6e472-118">Do seznamu by měla být přidána `fullTrustAssemblies` pouze sestavení, o kterých je známo, že jsou plně důvěryhodná.</span><span class="sxs-lookup"><span data-stu-id="6e472-118">Only assemblies known to be fully trusted should be added to the `fullTrustAssemblies` list.</span></span>  
  
 <span data-ttu-id="6e472-119">Přetížení má následující podpis:</span><span class="sxs-lookup"><span data-stu-id="6e472-119">The overload has the following signature:</span></span>  
  
```csharp
AppDomain.CreateDomain( string friendlyName,  
                        Evidence securityInfo,  
                        AppDomainSetup info,  
                        PermissionSet grantSet,  
                        params StrongName[] fullTrustAssemblies);  
```  
  
 <span data-ttu-id="6e472-120">Parametry pro <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> přetížení metody určují název <xref:System.AppDomain>, důkaz <xref:System.AppDomain>pro <xref:System.AppDomainSetup> , objekt, který identifikuje základnu aplikace pro izolovaného prostoru, sadu oprávnění k použití a silné názvy pro plně důvěryhodná sestavení.</span><span class="sxs-lookup"><span data-stu-id="6e472-120">The parameters for the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> method overload specify the name of the <xref:System.AppDomain>, the evidence for the <xref:System.AppDomain>, the <xref:System.AppDomainSetup> object that identifies the application base for the sandbox, the permission set to use, and the strong names for fully trusted assemblies.</span></span>  
  
 <span data-ttu-id="6e472-121">Z bezpečnostních důvodů by základ `info` aplikace zadaný v parametru neměl být základem aplikace pro hostitelskou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="6e472-121">For security reasons, the application base specified in the `info` parameter should not be the application base for the hosting application.</span></span>  
  
 <span data-ttu-id="6e472-122">Pro `grantSet` parametr můžete zadat buď sadu oprávnění, kterou jste explicitně vytvořili, nebo standardní sadu oprávnění vytvořenou <xref:System.Security.SecurityManager.GetStandardSandbox%2A> metodou.</span><span class="sxs-lookup"><span data-stu-id="6e472-122">For the `grantSet` parameter, you can specify either a permission set you have explicitly created, or a standard permission set created by the <xref:System.Security.SecurityManager.GetStandardSandbox%2A> method.</span></span>  
  
 <span data-ttu-id="6e472-123">Na <xref:System.AppDomain> rozdíl od většiny <xref:System.AppDomain> zatížení důkazy pro (který je k dispozici `securityInfo` parametr) se nepoužívá k určení sady grantů pro částečně důvěryhodná sestavení.</span><span class="sxs-lookup"><span data-stu-id="6e472-123">Unlike most <xref:System.AppDomain> loads, the evidence for the <xref:System.AppDomain> (which is provided by the `securityInfo` parameter) is not used to determine the grant set for the partially trusted assemblies.</span></span> <span data-ttu-id="6e472-124">Místo toho je nezávisle určen `grantSet` parametrem.</span><span class="sxs-lookup"><span data-stu-id="6e472-124">Instead, it is independently specified by the `grantSet` parameter.</span></span> <span data-ttu-id="6e472-125">Důkazy však mohou být použity pro jiné účely, jako je například určení rozsahu izolované úložiště.</span><span class="sxs-lookup"><span data-stu-id="6e472-125">However, the evidence can be used for other purposes such as determining the isolated storage scope.</span></span>  
  
### <a name="to-run-an-application-in-a-sandbox"></a><span data-ttu-id="6e472-126">Spuštění aplikace v izolovaném prostoru</span><span class="sxs-lookup"><span data-stu-id="6e472-126">To run an application in a sandbox</span></span>  
  
1. <span data-ttu-id="6e472-127">Vytvořte sadu oprávnění, která má být udělena nedůvěryhodné aplikaci.</span><span class="sxs-lookup"><span data-stu-id="6e472-127">Create the permission set to be granted to the untrusted application.</span></span> <span data-ttu-id="6e472-128">Minimální oprávnění, které <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> můžete udělit, je oprávnění.</span><span class="sxs-lookup"><span data-stu-id="6e472-128">The minimum permission you can grant is <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission.</span></span> <span data-ttu-id="6e472-129">Můžete také udělit další oprávnění, o kterých si myslíte, že mohou být pro nedůvěryhodný kód bezpečná. například <xref:System.Security.Permissions.IsolatedStorageFilePermission>.</span><span class="sxs-lookup"><span data-stu-id="6e472-129">You can also grant additional permissions you think might be safe for untrusted code; for example, <xref:System.Security.Permissions.IsolatedStorageFilePermission>.</span></span> <span data-ttu-id="6e472-130">Následující kód vytvoří novou sadu <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> oprávnění pouze s oprávněním.</span><span class="sxs-lookup"><span data-stu-id="6e472-130">The following code creates a new permission set with only <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission.</span></span>  
  
    ```csharp
    PermissionSet permSet = new PermissionSet(PermissionState.None);  
    permSet.AddPermission(new SecurityPermission(SecurityPermissionFlag.Execution));  
    ```  
  
     <span data-ttu-id="6e472-131">Případně můžete použít existující sadu pojmenovaných oprávnění, například Internet.</span><span class="sxs-lookup"><span data-stu-id="6e472-131">Alternatively, you can use an existing named permission set, such as Internet.</span></span>  
  
    ```csharp
    Evidence ev = new Evidence();  
    ev.AddHostEvidence(new Zone(SecurityZone.Internet));  
    PermissionSet internetPS = SecurityManager.GetStandardSandbox(ev);  
    ```  
  
     <span data-ttu-id="6e472-132">Metoda <xref:System.Security.SecurityManager.GetStandardSandbox%2A> vrátí sadu `Internet` oprávnění nebo `LocalIntranet` sadu oprávnění v závislosti na zóně v důkazech.</span><span class="sxs-lookup"><span data-stu-id="6e472-132">The <xref:System.Security.SecurityManager.GetStandardSandbox%2A> method returns either an `Internet` permission set or a `LocalIntranet` permission set depending on the zone in the evidence.</span></span> <span data-ttu-id="6e472-133"><xref:System.Security.SecurityManager.GetStandardSandbox%2A>také vytvoří oprávnění identity pro některé objekty legitimace předané jako odkazy.</span><span class="sxs-lookup"><span data-stu-id="6e472-133"><xref:System.Security.SecurityManager.GetStandardSandbox%2A> also constructs identity permissions for some of the evidence objects passed as references.</span></span>  
  
2. <span data-ttu-id="6e472-134">Podepište sestavení, které obsahuje `Sandboxer` třídu hostování (pojmenovanou v tomto příkladu), která volá nedůvěryhodný kód.</span><span class="sxs-lookup"><span data-stu-id="6e472-134">Sign the assembly that contains the hosting class (named `Sandboxer` in this example) that calls the untrusted code.</span></span> <span data-ttu-id="6e472-135">Přidejte <xref:System.Security.Policy.StrongName> slouží k podepsání <xref:System.Security.Policy.StrongName> sestavení `fullTrustAssemblies` do pole <xref:System.AppDomain.CreateDomain%2A> parametr volání.</span><span class="sxs-lookup"><span data-stu-id="6e472-135">Add the <xref:System.Security.Policy.StrongName> used to sign the assembly to the <xref:System.Security.Policy.StrongName> array of the `fullTrustAssemblies` parameter of the <xref:System.AppDomain.CreateDomain%2A> call.</span></span> <span data-ttu-id="6e472-136">Hostitelská třída musí být spuštěna jako plně důvěryhodná, aby bylo možné spustit kód částečné důvěryhodnosti nebo nabízet služby pro aplikaci s částečnou důvěryhodností.</span><span class="sxs-lookup"><span data-stu-id="6e472-136">The hosting class must run as fully trusted to enable the execution of the partial-trust code or to offer services to the partial-trust application.</span></span> <span data-ttu-id="6e472-137">To je, jak <xref:System.Security.Policy.StrongName> si přečíst sestavení:</span><span class="sxs-lookup"><span data-stu-id="6e472-137">This is how you read the <xref:System.Security.Policy.StrongName> of an assembly:</span></span>  
  
    ```csharp
    StrongName fullTrustAssembly = typeof(Sandboxer).Assembly.Evidence.GetHostEvidence<StrongName>();  
    ```  
  
     <span data-ttu-id="6e472-138">Sestavení rozhraní .NET Framework, jako jsou mscorlib a System.dll, nemusí být přidána do seznamu úplných vztahů důvěryhodnosti, protože jsou načtena jako plně důvěryhodná z globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="6e472-138">.NET Framework assemblies such as mscorlib and System.dll do not have to be added to the full-trust list because they are loaded as fully trusted from the global assembly cache.</span></span>  
  
3. <span data-ttu-id="6e472-139">Inicializovat <xref:System.AppDomainSetup> parametr <xref:System.AppDomain.CreateDomain%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="6e472-139">Initialize the <xref:System.AppDomainSetup> parameter of the <xref:System.AppDomain.CreateDomain%2A> method.</span></span> <span data-ttu-id="6e472-140">Pomocí tohoto parametru můžete řídit mnoho nastavení <xref:System.AppDomain>nového .</span><span class="sxs-lookup"><span data-stu-id="6e472-140">With this parameter, you can control many of the settings of the new <xref:System.AppDomain>.</span></span> <span data-ttu-id="6e472-141">Vlastnost <xref:System.AppDomainSetup.ApplicationBase%2A> je důležité nastavení a měla by <xref:System.AppDomainSetup.ApplicationBase%2A> se <xref:System.AppDomain> lišit od vlastnosti hostitelské aplikace.</span><span class="sxs-lookup"><span data-stu-id="6e472-141">The <xref:System.AppDomainSetup.ApplicationBase%2A> property is an important setting, and should be different from the <xref:System.AppDomainSetup.ApplicationBase%2A> property for the <xref:System.AppDomain> of the hosting application.</span></span> <span data-ttu-id="6e472-142">Pokud <xref:System.AppDomainSetup.ApplicationBase%2A> jsou nastavení stejná, aplikace s částečnou důvěryhodností může získat hostitelskou aplikaci k načtení (jako plně důvěryhodné) výjimku, kterou definuje, a tím ji zneužít.</span><span class="sxs-lookup"><span data-stu-id="6e472-142">If the <xref:System.AppDomainSetup.ApplicationBase%2A> settings are the same, the partial-trust application can get the hosting application to load (as fully trusted) an exception it defines, thus exploiting it.</span></span> <span data-ttu-id="6e472-143">To je další důvod, proč se nedoporučuje catch (výjimka).</span><span class="sxs-lookup"><span data-stu-id="6e472-143">This is another reason why a catch (exception) is not recommended.</span></span> <span data-ttu-id="6e472-144">Nastavení základu aplikace hostitele odlišně od základu aplikace aplikace v izolovaném prostoru zmírňuje riziko zneužití.</span><span class="sxs-lookup"><span data-stu-id="6e472-144">Setting the application base of the host differently from the application base of the sandboxed application mitigates the risk of exploits.</span></span>  
  
    ```csharp
    AppDomainSetup adSetup = new AppDomainSetup();  
    adSetup.ApplicationBase = Path.GetFullPath(pathToUntrusted);  
    ```  
  
4. <span data-ttu-id="6e472-145">Volání <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> přetížení metody k vytvoření domény aplikace pomocí parametrů, které jsme zadali.</span><span class="sxs-lookup"><span data-stu-id="6e472-145">Call the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> method overload to create the application domain using the parameters we have specified.</span></span>  
  
     <span data-ttu-id="6e472-146">Podpis pro tuto metodu je:</span><span class="sxs-lookup"><span data-stu-id="6e472-146">The signature for this method is:</span></span>  
  
    ```csharp
    public static AppDomain CreateDomain(string friendlyName,
        Evidence securityInfo, AppDomainSetup info, PermissionSet grantSet,
        params StrongName[] fullTrustAssemblies)  
    ```  
  
     <span data-ttu-id="6e472-147">Další informace:</span><span class="sxs-lookup"><span data-stu-id="6e472-147">Additional information:</span></span>  
  
    - <span data-ttu-id="6e472-148">Toto je pouze <xref:System.AppDomain.CreateDomain%2A> přetížení metody, <xref:System.Security.PermissionSet> která trvá jako parametr a tedy pouze přetížení, které umožňuje načíst aplikaci v nastavení částečné důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="6e472-148">This is the only overload of the <xref:System.AppDomain.CreateDomain%2A> method that takes a <xref:System.Security.PermissionSet> as a parameter, and thus the only overload that lets you load an application in a partial-trust setting.</span></span>  
  
    - <span data-ttu-id="6e472-149">Parametr `evidence` se nepoužívá k výpočtu sady oprávnění. používá se pro identifikaci jinými funkcemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6e472-149">The `evidence` parameter is not used to calculate a permission set; it is used for identification by other features of the .NET Framework.</span></span>  
  
    - <span data-ttu-id="6e472-150">Nastavení <xref:System.AppDomainSetup.ApplicationBase%2A> vlastnosti `info` parametru je pro toto přetížení povinné.</span><span class="sxs-lookup"><span data-stu-id="6e472-150">Setting the <xref:System.AppDomainSetup.ApplicationBase%2A> property of the `info` parameter is mandatory for this overload.</span></span>  
  
    - <span data-ttu-id="6e472-151">Parametr `fullTrustAssemblies` má `params` klíčové slovo, což znamená, že <xref:System.Security.Policy.StrongName> není nutné vytvořit pole.</span><span class="sxs-lookup"><span data-stu-id="6e472-151">The `fullTrustAssemblies` parameter has the `params` keyword, which means that it is not necessary to create a <xref:System.Security.Policy.StrongName> array.</span></span> <span data-ttu-id="6e472-152">Předávání 0, 1 nebo více silných názvů jako parametry je povoleno.</span><span class="sxs-lookup"><span data-stu-id="6e472-152">Passing 0, 1, or more strong names as parameters is allowed.</span></span>  
  
    - <span data-ttu-id="6e472-153">Kód pro vytvoření domény aplikace je:</span><span class="sxs-lookup"><span data-stu-id="6e472-153">The code to create the application domain is:</span></span>  
  
    ```csharp
    AppDomain newDomain = AppDomain.CreateDomain("Sandbox", null, adSetup, permSet, fullTrustAssembly);  
    ```  
  
5. <span data-ttu-id="6e472-154">Načtěte kód do <xref:System.AppDomain> izolovaného prostoru, který jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="6e472-154">Load the code into the sandboxing <xref:System.AppDomain> that you created.</span></span> <span data-ttu-id="6e472-155">To lze provést dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="6e472-155">This can be done in two ways:</span></span>  
  
    - <span data-ttu-id="6e472-156">Volání <xref:System.AppDomain.ExecuteAssembly%2A> metody pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="6e472-156">Call the <xref:System.AppDomain.ExecuteAssembly%2A> method for the assembly.</span></span>  
  
    - <span data-ttu-id="6e472-157">Pomocí <xref:System.Activator.CreateInstanceFrom%2A> metody vytvořte instanci třídy <xref:System.MarshalByRefObject> odvozené <xref:System.AppDomain>z nové .</span><span class="sxs-lookup"><span data-stu-id="6e472-157">Use the <xref:System.Activator.CreateInstanceFrom%2A> method to create an instance of a class derived from <xref:System.MarshalByRefObject> in the new <xref:System.AppDomain>.</span></span>  
  
     <span data-ttu-id="6e472-158">Druhá metoda je vhodnější, protože usnadňuje předávání parametrů do <xref:System.AppDomain> nové instance.</span><span class="sxs-lookup"><span data-stu-id="6e472-158">The second method is preferable, because it makes it easier to pass parameters to the new <xref:System.AppDomain> instance.</span></span> <span data-ttu-id="6e472-159">Metoda <xref:System.Activator.CreateInstanceFrom%2A> poskytuje dvě důležité funkce:</span><span class="sxs-lookup"><span data-stu-id="6e472-159">The <xref:System.Activator.CreateInstanceFrom%2A> method provides two important features:</span></span>  
  
    - <span data-ttu-id="6e472-160">Můžete použít základ kódu, který odkazuje na umístění, které neobsahuje vaše sestavení.</span><span class="sxs-lookup"><span data-stu-id="6e472-160">You can use a code base that points to a location that does not contain your assembly.</span></span>  
  
    - <span data-ttu-id="6e472-161">Vytvoření můžete provést v <xref:System.Security.CodeAccessPermission.Assert%2A> rámci pro<xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType>plnou důvěryhodnost ( ), která umožňuje vytvořit instanci kritické třídy.</span><span class="sxs-lookup"><span data-stu-id="6e472-161">You can do the creation under an <xref:System.Security.CodeAccessPermission.Assert%2A> for full-trust (<xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType>), which enables you to create an instance of a critical class.</span></span> <span data-ttu-id="6e472-162">(K tomu dochází vždy, když vaše sestava nemá žádné označení průhlednosti a je načtena jako plně důvěryhodná.) Proto musíte být opatrní vytvořit pouze kód, kterému důvěřujete s touto funkcí a doporučujeme vytvořit pouze instance plně důvěryhodné třídy v nové doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="6e472-162">(This happens whenever your assembly has no transparency markings and is loaded as fully trusted.) Therefore, you have to be careful to create only code that you trust with this function, and we recommend that you create only instances of fully trusted classes in the new application domain.</span></span>  
  
    ```csharp
    ObjectHandle handle = Activator.CreateInstanceFrom(  
    newDomain, typeof(Sandboxer).Assembly.ManifestModule.FullyQualifiedName,  
           typeof(Sandboxer).FullName );  
    ```  
  
     <span data-ttu-id="6e472-163">Všimněte si, že k vytvoření instance třídy v nové doméně, třída musí rozšířit třídu <xref:System.MarshalByRefObject></span><span class="sxs-lookup"><span data-stu-id="6e472-163">Note that in order to create an instance of a class in a new domain, the class has to extend the <xref:System.MarshalByRefObject> class</span></span>  
  
    ```csharp
    class Sandboxer:MarshalByRefObject  
    ```  
  
6. <span data-ttu-id="6e472-164">Rozbalte novou instanci domény do odkazu v této doméně.</span><span class="sxs-lookup"><span data-stu-id="6e472-164">Unwrap the new domain instance into a reference in this domain.</span></span> <span data-ttu-id="6e472-165">Tento odkaz se používá ke spuštění nedůvěryhodného kódu.</span><span class="sxs-lookup"><span data-stu-id="6e472-165">This reference is used to execute the untrusted code.</span></span>  
  
    ```csharp
    Sandboxer newDomainInstance = (Sandboxer) handle.Unwrap();  
    ```  
  
7. <span data-ttu-id="6e472-166">Volání `ExecuteUntrustedCode` metody v instanci třídy, kterou `Sandboxer` jste právě vytvořili.</span><span class="sxs-lookup"><span data-stu-id="6e472-166">Call the `ExecuteUntrustedCode` method in the instance of the `Sandboxer` class you just created.</span></span>  
  
    ```csharp
    newDomainInstance.ExecuteUntrustedCode(untrustedAssembly, untrustedClass, entryPoint, parameters);  
    ```  
  
     <span data-ttu-id="6e472-167">Toto volání je provedeno v doméně aplikace v izolovaném prostoru, která má omezená oprávnění.</span><span class="sxs-lookup"><span data-stu-id="6e472-167">This call is executed in the sandboxed application domain, which has restricted permissions.</span></span>  
  
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
  
     <span data-ttu-id="6e472-168"><xref:System.Reflection>se používá k získání popisovače metody v částečně důvěryhodném sestavení.</span><span class="sxs-lookup"><span data-stu-id="6e472-168"><xref:System.Reflection> is used to get a handle of a method in the partially trusted assembly.</span></span> <span data-ttu-id="6e472-169">Popisovač lze spustit kód bezpečným způsobem s minimálními oprávněními.</span><span class="sxs-lookup"><span data-stu-id="6e472-169">The handle can be used to execute code in a safe way with minimum permissions.</span></span>  
  
     <span data-ttu-id="6e472-170">V předchozím kódu si <xref:System.Security.PermissionSet.Assert%2A> před tiskem aplikace všimněte plné důvěryhodnosti <xref:System.Security.SecurityException>oprávnění pro úplnou důvěryhodnost.</span><span class="sxs-lookup"><span data-stu-id="6e472-170">In the previous code, note the <xref:System.Security.PermissionSet.Assert%2A> for the full-trust permission before printing the <xref:System.Security.SecurityException>.</span></span>  
  
    ```csharp
    new PermissionSet(PermissionState.Unrestricted).Assert()  
    ```  
  
     <span data-ttu-id="6e472-171">Plně důvěryhodné assert se používá k získání <xref:System.Security.SecurityException>rozšířené informace z .</span><span class="sxs-lookup"><span data-stu-id="6e472-171">The full-trust assert is used to obtain extended information from the <xref:System.Security.SecurityException>.</span></span> <span data-ttu-id="6e472-172">Bez <xref:System.Security.PermissionSet.Assert%2A>, <xref:System.Security.SecurityException.ToString%2A> metoda <xref:System.Security.SecurityException> zjistíte, že je částečně důvěryhodný kód v zásobníku a omezí vrácené informace.</span><span class="sxs-lookup"><span data-stu-id="6e472-172">Without the <xref:System.Security.PermissionSet.Assert%2A>, the <xref:System.Security.SecurityException.ToString%2A> method of <xref:System.Security.SecurityException> will discover that there is partially trusted code on the stack and will restrict the information returned.</span></span> <span data-ttu-id="6e472-173">To by mohlo způsobit problémy se zabezpečením, pokud kód částečné důvěryhodnosti <xref:System.Security.Permissions.UIPermission>může číst tyto informace, ale riziko je zmírněno tím, že neuděluje .</span><span class="sxs-lookup"><span data-stu-id="6e472-173">This could cause security issues if the partial-trust code could read that information, but the risk is mitigated by not granting <xref:System.Security.Permissions.UIPermission>.</span></span> <span data-ttu-id="6e472-174">Full-trust assert by měl být používán střídmě a pouze v případě, že jste si jisti, že nepovolujete kód částečné důvěryhodnosti, aby se zvýšil na úplný vztah důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="6e472-174">The full-trust assert should be used sparingly and only when you are sure that you are not allowing partial-trust code to elevate to full trust.</span></span> <span data-ttu-id="6e472-175">Zpravidla nevolejte kód, kterému nedůvěřujete ve stejné funkci, a poté, co jste zavolali assert pro úplný vztah důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="6e472-175">As a rule, do not call code you do not trust in the same function and after you called an assert for full trust.</span></span> <span data-ttu-id="6e472-176">Je vhodné vždy vrátit assert po dokončení jeho použití.</span><span class="sxs-lookup"><span data-stu-id="6e472-176">It is good practice to always revert the assert when you have finished using it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e472-177">Příklad</span><span class="sxs-lookup"><span data-stu-id="6e472-177">Example</span></span>  
 <span data-ttu-id="6e472-178">Následující příklad implementuje postup v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="6e472-178">The following example implements the procedure in the previous section.</span></span> <span data-ttu-id="6e472-179">V příkladu projekt `Sandboxer` s názvem v řešení sady `UntrustedCode`Visual Studio také `UntrustedClass`obsahuje projekt s názvem , který implementuje třídu .</span><span class="sxs-lookup"><span data-stu-id="6e472-179">In the example, a project named `Sandboxer` in a Visual Studio solution also contains a project named `UntrustedCode`, which implements the class `UntrustedClass`.</span></span> <span data-ttu-id="6e472-180">Tento scénář předpokládá, že jste stáhli sestavení knihovny obsahující `true` metodu, která se očekává, že se vrátí nebo `false` označuje, zda je zadaným číslem Fibonacciho číslo.</span><span class="sxs-lookup"><span data-stu-id="6e472-180">This scenario assumes that you have downloaded a library assembly containing a method that is expected to return `true` or `false` to indicate whether the number you provided is a Fibonacci number.</span></span> <span data-ttu-id="6e472-181">Místo toho se metoda pokusí číst soubor z počítače.</span><span class="sxs-lookup"><span data-stu-id="6e472-181">Instead, the method attempts to read a file from your computer.</span></span> <span data-ttu-id="6e472-182">Následující příklad ukazuje nedůvěryhodný kód.</span><span class="sxs-lookup"><span data-stu-id="6e472-182">The following example shows the untrusted code.</span></span>  
  
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
  
 <span data-ttu-id="6e472-183">Následující příklad ukazuje `Sandboxer` kód aplikace, který spustí nedůvěryhodný kód.</span><span class="sxs-lookup"><span data-stu-id="6e472-183">The following example shows the `Sandboxer` application code that executes the untrusted code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6e472-184">Viz také</span><span class="sxs-lookup"><span data-stu-id="6e472-184">See also</span></span>

- [<span data-ttu-id="6e472-185">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="6e472-185">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
