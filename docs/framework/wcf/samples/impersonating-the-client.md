---
title: Zosobnění klienta
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, impersonation sample
- Impersonating the Client Sample [Windows Communication Foundation]
- impersonation, Windows Communication Foundation sample
ms.assetid: 8bd974e1-90db-4152-95a3-1d4b1a7734f8
ms.openlocfilehash: 61befdcaf1381120dba6f72ba592dade09d0490a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968343"
---
# <a name="impersonating-the-client"></a><span data-ttu-id="35446-102">Zosobnění klienta</span><span class="sxs-lookup"><span data-stu-id="35446-102">Impersonating the Client</span></span>
<span data-ttu-id="35446-103">Ukázka zosobnění ukazuje, jak zosobnit volající aplikaci ve službě, aby služba mohla přistupovat k systémovým prostředkům jménem volajícího.</span><span class="sxs-lookup"><span data-stu-id="35446-103">The Impersonation sample demonstrates how to impersonate the caller application at the service so that the service can access system resources on behalf of the caller.</span></span>  
  
 <span data-ttu-id="35446-104">Tato ukázka je založená na ukázce [samostatného hostitele](../../../../docs/framework/wcf/samples/self-host.md) .</span><span class="sxs-lookup"><span data-stu-id="35446-104">This sample is based on the [Self-Host](../../../../docs/framework/wcf/samples/self-host.md) sample.</span></span> <span data-ttu-id="35446-105">Konfigurační soubory služby a klienta jsou stejné jako v ukázce [samostatného hostitele](../../../../docs/framework/wcf/samples/self-host.md) .</span><span class="sxs-lookup"><span data-stu-id="35446-105">The service and client configuration files are the same as that of the [Self-Host](../../../../docs/framework/wcf/samples/self-host.md) sample.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="35446-106">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="35446-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="35446-107">Kód služby byl změněn tak, aby `Add` metoda ve službě zosobňuje volajícího <xref:System.ServiceModel.OperationBehaviorAttribute> pomocí metody, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="35446-107">The service code has been modified such that the `Add` method on the service impersonates the caller using the <xref:System.ServiceModel.OperationBehaviorAttribute> as shown in the following sample code.</span></span>  
  
```csharp
[OperationBehavior(Impersonation = ImpersonationOption.Required)]  
public double Add(double n1, double n2)  
{  
    double result = n1 + n2;  
    Console.WriteLine("Received Add({0},{1})", n1, n2);  
    Console.WriteLine("Return: {0}", result);  
    DisplayIdentityInformation();  
    return result;  
}  
```  
  
 <span data-ttu-id="35446-108">V důsledku toho je kontext zabezpečení vykonávajícího vlákna přepnut na zosobnění volajícího před vstupem `Add` metody a při ukončení metody se vrátil zpět.</span><span class="sxs-lookup"><span data-stu-id="35446-108">As a result, the security context of the executing thread is switched to impersonate the caller before entering the `Add` method and reverted on exiting the method.</span></span>  
  
 <span data-ttu-id="35446-109">`DisplayIdentityInformation` Metoda zobrazená v následujícím ukázkovém kódu je funkce nástroje, která zobrazuje identitu volajícího.</span><span class="sxs-lookup"><span data-stu-id="35446-109">The `DisplayIdentityInformation` method shown in the following sample code is a utility function that displays the caller's identity.</span></span>  
  
```csharp
static void DisplayIdentityInformation()  
{  
    Console.WriteLine("\t\tThread Identity            :{0}",  
         WindowsIdentity.GetCurrent().Name);  
    Console.WriteLine("\t\tThread Identity level  :{0}",   
         WindowsIdentity.GetCurrent().ImpersonationLevel);  
    Console.WriteLine("\t\thToken                     :{0}",  
         WindowsIdentity.GetCurrent().Token.ToString());  
    return;  
}  
```  
  
 <span data-ttu-id="35446-110">`Subtract` Metoda ve službě zosobňuje volajícího pomocí imperativních volání, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="35446-110">The `Subtract` method on the service impersonates the caller using imperative calls as shown in the following sample code.</span></span>  
  
```csharp
public double Subtract(double n1, double n2)  
{  
    double result = n1 - n2;  
    Console.WriteLine("Received Subtract({0},{1})", n1, n2);  
    Console.WriteLine("Return: {0}", result);  
    Console.WriteLine("Before impersonating");  
    DisplayIdentityInformation();  
  
    if (ServiceSecurityContext.Current.WindowsIdentity.ImpersonationLevel == TokenImpersonationLevel.Impersonation ||  
        ServiceSecurityContext.Current.WindowsIdentity.ImpersonationLevel == TokenImpersonationLevel.Delegation)  
    {  
        // Impersonate.  
        using (ServiceSecurityContext.Current.WindowsIdentity.Impersonate())  
        {  
            // Make a system call in the caller's context and ACLs   
            // on the system resource are enforced in the caller's context.   
            Console.WriteLine("Impersonating the caller imperatively");  
            DisplayIdentityInformation();  
        }  
    }  
    else  
    {  
        Console.WriteLine("ImpersonationLevel is not high enough to perform this operation.");  
    }  
  
    Console.WriteLine("After reverting");  
    DisplayIdentityInformation();  
    return result;  
}  
```  
  
 <span data-ttu-id="35446-111">Všimněte si, že v tomto případě volající není zosobněn pro celé volání, ale je zosobněna pouze pro část volání.</span><span class="sxs-lookup"><span data-stu-id="35446-111">Note that in this case the caller is not impersonated for the entire call but is only impersonated for a portion of the call.</span></span> <span data-ttu-id="35446-112">Obecně platí, že zosobnění pro nejmenší rozsah je vhodnější pro zosobnění pro celou operaci.</span><span class="sxs-lookup"><span data-stu-id="35446-112">In general, impersonating for the smallest scope is preferable to impersonating for the entire operation.</span></span>  
  
 <span data-ttu-id="35446-113">Jiné metody nezosobňuje volajícího.</span><span class="sxs-lookup"><span data-stu-id="35446-113">The other methods do not impersonate the caller.</span></span>  
  
 <span data-ttu-id="35446-114">Kód klienta byl upraven, aby bylo možné nastavit úroveň zosobnění na <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>hodnotu.</span><span class="sxs-lookup"><span data-stu-id="35446-114">The client code has been modified to set the impersonation level to <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>.</span></span> <span data-ttu-id="35446-115">Klient Určuje úroveň zosobnění, kterou bude služba používat, pomocí <xref:System.Security.Principal.TokenImpersonationLevel> výčtu.</span><span class="sxs-lookup"><span data-stu-id="35446-115">The client specifies the impersonation level to be used by the service, by using the <xref:System.Security.Principal.TokenImpersonationLevel> enumeration.</span></span> <span data-ttu-id="35446-116">Výčet podporuje následující hodnoty: <xref:System.Security.Principal.TokenImpersonationLevel.None>, <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, <xref:System.Security.Principal.TokenImpersonationLevel.Identification> <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> a.<xref:System.Security.Principal.TokenImpersonationLevel.Delegation></span><span class="sxs-lookup"><span data-stu-id="35446-116">The enumeration supports the following values: <xref:System.Security.Principal.TokenImpersonationLevel.None>, <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, <xref:System.Security.Principal.TokenImpersonationLevel.Identification>, <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> and <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>.</span></span> <span data-ttu-id="35446-117">Chcete-li provést kontrolu přístupu při přístupu k systémovému prostředku v místním počítači, který je chráněn pomocí seznamů řízení přístupu systému Windows, musí být úroveň zosobnění nastavena na <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="35446-117">To perform an access check when accessing a system resource on the local machine that is protected using Windows ACLs, the impersonation level must be set to <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>, as shown in the following sample code.</span></span>  
  
```csharp
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
client.ClientCredentials.Windows.AllowedImpersonationLevel = TokenImpersonationLevel.Impersonation;  
```  
  
 <span data-ttu-id="35446-118">Při spuštění ukázky se požadavky na operace a odpovědi zobrazí v oknech služba i klientská konzola.</span><span class="sxs-lookup"><span data-stu-id="35446-118">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="35446-119">V každém okně konzoly stiskněte klávesu ENTER a ukončete službu a klienta.</span><span class="sxs-lookup"><span data-stu-id="35446-119">Press ENTER in each console window to shut down the service and client.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="35446-120">Služba musí běžet buď pod účtem správce, nebo účtem, ve kterém je spuštěný, musí mít udělena práva k `http://localhost:8000/ServiceModelSamples` registraci identifikátoru URI ve vrstvě http.</span><span class="sxs-lookup"><span data-stu-id="35446-120">The service must either run under an administrative account or the account it runs under must be granted rights to register the `http://localhost:8000/ServiceModelSamples` URI with the HTTP layer.</span></span> <span data-ttu-id="35446-121">Taková práva je možné udělit nastavením [rezervace oboru názvů](https://go.microsoft.com/fwlink/?LinkId=95012) pomocí [nástroje HttpCfg. exe](https://go.microsoft.com/fwlink/?LinkId=95010).</span><span class="sxs-lookup"><span data-stu-id="35446-121">Such rights can be granted by setting up a [Namespace Reservation](https://go.microsoft.com/fwlink/?LinkId=95012) using the [Httpcfg.exe tool](https://go.microsoft.com/fwlink/?LinkId=95010).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="35446-122">V počítačích se [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]systémem se zosobnění podporuje jenom v případě, že má aplikace Host. exe oprávnění k zosobnění.</span><span class="sxs-lookup"><span data-stu-id="35446-122">On computers running [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], impersonation is supported only if the Host.exe application has the Impersonation privilege.</span></span> <span data-ttu-id="35446-123">(Ve výchozím nastavení mají toto oprávnění pouze správci.) Pokud chcete toto oprávnění přidat k účtu, ve kterém je služba spuštěná, přejděte do části **Nástroje pro správu**, otevřete **místní zásady zabezpečení**, otevřete **místní zásady**, klikněte na **přiřazení uživatelských práv**a vyberte **zosobnit klienta po Ověřování** a dvojím kliknutím na **vlastnosti** můžete přidat uživatele nebo skupinu.</span><span class="sxs-lookup"><span data-stu-id="35446-123">(By default, only administrators have this permission.) To add this privilege to an account the service is running as, go to **Administrative Tools**, open **Local Security Policy**, open **Local Policies**, click **User Rights Assignment**, and select **Impersonate a Client after Authentication** and double-click **Properties** to add a user or group.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="35446-124">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="35446-124">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="35446-125">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="35446-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="35446-126">Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="35446-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="35446-127">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="35446-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
4. <span data-ttu-id="35446-128">Chcete-li předvést, že služba zosobňuje volajícího, spusťte klienta pod jiným účtem, než je služba spuštěná.</span><span class="sxs-lookup"><span data-stu-id="35446-128">To demonstrate that the service impersonates the caller, run the client under a different account than the one the service is running under.</span></span> <span data-ttu-id="35446-129">Uděláte to tak, že na příkazovém řádku zadáte:</span><span class="sxs-lookup"><span data-stu-id="35446-129">To do so, at the command prompt, type:</span></span>  
  
    ```  
    runas /user:<machine-name>\<user-name> client.exe  
    ```  
  
     <span data-ttu-id="35446-130">Pak se zobrazí výzva k zadání hesla.</span><span class="sxs-lookup"><span data-stu-id="35446-130">You are then prompted for a password.</span></span> <span data-ttu-id="35446-131">Zadejte heslo pro účet, který jste zadali dříve.</span><span class="sxs-lookup"><span data-stu-id="35446-131">Enter the password for the account you previously specified.</span></span>  
  
5. <span data-ttu-id="35446-132">Když spustíte klienta, poznamenejte si identitu před a po spuštění s jinými přihlašovacími údaji.</span><span class="sxs-lookup"><span data-stu-id="35446-132">When you run the client, note the identity before and after running it with different credentials.</span></span>  
