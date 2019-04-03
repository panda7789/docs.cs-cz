---
title: Zosobnění klienta
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, impersonation sample
- Impersonating the Client Sample [Windows Communication Foundation]
- impersonation, Windows Communication Foundation sample
ms.assetid: 8bd974e1-90db-4152-95a3-1d4b1a7734f8
ms.openlocfilehash: 8338d04382e77c231232ca2080c21e8732a683b7
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58836126"
---
# <a name="impersonating-the-client"></a><span data-ttu-id="54161-102">Zosobnění klienta</span><span class="sxs-lookup"><span data-stu-id="54161-102">Impersonating the Client</span></span>
<span data-ttu-id="54161-103">Ukázka zosobnění ukazuje, jak zosobnit volající aplikace na službu tak, aby službě můžete získat přístup k systémovým prostředkům jménem volající.</span><span class="sxs-lookup"><span data-stu-id="54161-103">The Impersonation sample demonstrates how to impersonate the caller application at the service so that the service can access system resources on behalf of the caller.</span></span>  
  
 <span data-ttu-id="54161-104">Tato ukázka je založena na [hostování na vlastním serveru](../../../../docs/framework/wcf/samples/self-host.md) vzorku.</span><span class="sxs-lookup"><span data-stu-id="54161-104">This sample is based on the [Self-Host](../../../../docs/framework/wcf/samples/self-host.md) sample.</span></span> <span data-ttu-id="54161-105">Konfigurační soubory klienta a služby jsou stejné jako u [hostování na vlastním serveru](../../../../docs/framework/wcf/samples/self-host.md) vzorku.</span><span class="sxs-lookup"><span data-stu-id="54161-105">The service and client configuration files are the same as that of the [Self-Host](../../../../docs/framework/wcf/samples/self-host.md) sample.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="54161-106">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="54161-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="54161-107">Kód služby byla změněna tak, aby `Add` zosobňuje volající pomocí metody ve službě <xref:System.ServiceModel.OperationBehaviorAttribute> jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="54161-107">The service code has been modified such that the `Add` method on the service impersonates the caller using the <xref:System.ServiceModel.OperationBehaviorAttribute> as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="54161-108">V důsledku toho přepnutí kontextu zabezpečení spuštěné vlákno na zosobňují volajícího před vstupem `Add` metoda a vrátit zpět k ukončení metodu.</span><span class="sxs-lookup"><span data-stu-id="54161-108">As a result, the security context of the executing thread is switched to impersonate the caller before entering the `Add` method and reverted on exiting the method.</span></span>  
  
 <span data-ttu-id="54161-109">`DisplayIdentityInformation` Metoda je znázorněno v následujícím ukázkovém kódu je nástroj pro funkci, která zobrazuje identitu volajícího.</span><span class="sxs-lookup"><span data-stu-id="54161-109">The `DisplayIdentityInformation` method shown in the following sample code is a utility function that displays the caller's identity.</span></span>  
  
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
  
 <span data-ttu-id="54161-110">`Subtract` Metoda ve službě zosobňuje volající pomocí imperativního volání, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="54161-110">The `Subtract` method on the service impersonates the caller using imperative calls as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="54161-111">Všimněte si, že v tomto případě volající není zosobnit celý volání, ale je jen zosobněné část volání.</span><span class="sxs-lookup"><span data-stu-id="54161-111">Note that in this case the caller is not impersonated for the entire call but is only impersonated for a portion of the call.</span></span> <span data-ttu-id="54161-112">Zosobnění pro nejmenší obor je obecně vhodnější zosobnění pro celou operaci.</span><span class="sxs-lookup"><span data-stu-id="54161-112">In general, impersonating for the smallest scope is preferable to impersonating for the entire operation.</span></span>  
  
 <span data-ttu-id="54161-113">Jiné metody není zosobňují volajícího.</span><span class="sxs-lookup"><span data-stu-id="54161-113">The other methods do not impersonate the caller.</span></span>  
  
 <span data-ttu-id="54161-114">Klientský kód byl změněn na nastavení úrovně k zosobnění <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>.</span><span class="sxs-lookup"><span data-stu-id="54161-114">The client code has been modified to set the impersonation level to <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>.</span></span> <span data-ttu-id="54161-115">Určuje úroveň zosobnění použije službu, pomocí klienta <xref:System.Security.Principal.TokenImpersonationLevel> výčtu.</span><span class="sxs-lookup"><span data-stu-id="54161-115">The client specifies the impersonation level to be used by the service, by using the <xref:System.Security.Principal.TokenImpersonationLevel> enumeration.</span></span> <span data-ttu-id="54161-116">Výčet podporuje následující hodnoty: <xref:System.Security.Principal.TokenImpersonationLevel.None>, <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, <xref:System.Security.Principal.TokenImpersonationLevel.Identification>, <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> a <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>.</span><span class="sxs-lookup"><span data-stu-id="54161-116">The enumeration supports the following values: <xref:System.Security.Principal.TokenImpersonationLevel.None>, <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, <xref:System.Security.Principal.TokenImpersonationLevel.Identification>, <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> and <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>.</span></span> <span data-ttu-id="54161-117">K provedení kontroly přístupu při přístupu k systémového prostředku v místním počítači, který je chráněn pomocí ACL Windows, musí být nastavena úroveň zosobnění <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="54161-117">To perform an access check when accessing a system resource on the local machine that is protected using Windows ACLs, the impersonation level must be set to <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>, as shown in the following sample code.</span></span>  
  
```csharp
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
client.ClientCredentials.Windows.AllowedImpersonationLevel = TokenImpersonationLevel.Impersonation;  
```  
  
 <span data-ttu-id="54161-118">Při spuštění ukázky operace žádosti a odpovědi se zobrazují v oknech konzoly služby a klienta.</span><span class="sxs-lookup"><span data-stu-id="54161-118">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="54161-119">Stisknutím klávesy ENTER v každé okno konzoly pro vypnutí klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="54161-119">Press ENTER in each console window to shut down the service and client.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="54161-120">Služba se musí buď spustit pod účtem správce nebo účet běží pod musí mít udělena oprávnění k registraci `http://localhost:8000/ServiceModelSamples` identifikátor URI s vrstvou HTTP.</span><span class="sxs-lookup"><span data-stu-id="54161-120">The service must either run under an administrative account or the account it runs under must be granted rights to register the `http://localhost:8000/ServiceModelSamples` URI with the HTTP layer.</span></span> <span data-ttu-id="54161-121">Tato oprávnění lze udělit nastavením [Namespace rezervace](https://go.microsoft.com/fwlink/?LinkId=95012) pomocí [Httpcfg.exe nástroj](https://go.microsoft.com/fwlink/?LinkId=95010).</span><span class="sxs-lookup"><span data-stu-id="54161-121">Such rights can be granted by setting up a [Namespace Reservation](https://go.microsoft.com/fwlink/?LinkId=95012) using the [Httpcfg.exe tool](https://go.microsoft.com/fwlink/?LinkId=95010).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="54161-122">V počítačích se systémem [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], zosobnění je podporována pouze v případě, že aplikace Host.exe má oprávnění k zosobnění.</span><span class="sxs-lookup"><span data-stu-id="54161-122">On computers running [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], impersonation is supported only if the Host.exe application has the Impersonation privilege.</span></span> <span data-ttu-id="54161-123">(Ve výchozím nastavení, pouze správci mají toto oprávnění.) Pokud chcete přidat toto oprávnění je služba spuštěna jako účet, přejděte na **nástroje pro správu**, otevřete **místní zásady zabezpečení**, otevřete **místní zásady**, klikněte na tlačítko **Přiřazení uživatelských práv**a vyberte **zosobnit klienta po ověření** a dvakrát klikněte na panel **vlastnosti** přidat uživatele nebo skupinu.</span><span class="sxs-lookup"><span data-stu-id="54161-123">(By default, only administrators have this permission.) To add this privilege to an account the service is running as, go to **Administrative Tools**, open **Local Security Policy**, open **Local Policies**, click **User Rights Assignment**, and select **Impersonate a Client after Authentication** and double-click **Properties** to add a user or group.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="54161-124">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="54161-124">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="54161-125">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="54161-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="54161-126">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="54161-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="54161-127">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="54161-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="54161-128">Abychom si předvedli, že služba zosobňuje volajícího, spustíte klienta pod jiným účtem než ten, který je služba spuštěná pod.</span><span class="sxs-lookup"><span data-stu-id="54161-128">To demonstrate that the service impersonates the caller, run the client under a different account than the one the service is running under.</span></span> <span data-ttu-id="54161-129">Provedete to tak, že na příkazovém řádku zadejte:</span><span class="sxs-lookup"><span data-stu-id="54161-129">To do so, at the command prompt, type:</span></span>  
  
    ```  
    runas /user:<machine-name>\<user-name> client.exe  
    ```  
  
     <span data-ttu-id="54161-130">Zobrazí se výzva k zadání hesla.</span><span class="sxs-lookup"><span data-stu-id="54161-130">You are then prompted for a password.</span></span> <span data-ttu-id="54161-131">Zadejte heslo pro účet, který jste dříve zadali.</span><span class="sxs-lookup"><span data-stu-id="54161-131">Enter the password for the account you previously specified.</span></span>  
  
5.  <span data-ttu-id="54161-132">Když spustíte klienta, si povšimněte identity před a po spuštění s jinými přihlašovacími údaji.</span><span class="sxs-lookup"><span data-stu-id="54161-132">When you run the client, note the identity before and after running it with different credentials.</span></span>  
  
