---
title: Zosobnění klienta
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, impersonation sample
- Impersonating the Client Sample [Windows Communication Foundation]
- impersonation, Windows Communication Foundation sample
ms.assetid: 8bd974e1-90db-4152-95a3-1d4b1a7734f8
ms.openlocfilehash: 4c5d911bfbfcd33248e15b9fc822abdc9cf4046c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33505007"
---
# <a name="impersonating-the-client"></a><span data-ttu-id="192cc-102">Zosobnění klienta</span><span class="sxs-lookup"><span data-stu-id="192cc-102">Impersonating the Client</span></span>
<span data-ttu-id="192cc-103">Ukázka zosobnění ukazuje, jak zosobnit volající aplikace ve službě, aby služba přístup jménem volající systémové prostředky.</span><span class="sxs-lookup"><span data-stu-id="192cc-103">The Impersonation sample demonstrates how to impersonate the caller application at the service so that the service can access system resources on behalf of the caller.</span></span>  
  
 <span data-ttu-id="192cc-104">Tato ukázka je založena na [hostování na vlastním](../../../../docs/framework/wcf/samples/self-host.md) ukázka.</span><span class="sxs-lookup"><span data-stu-id="192cc-104">This sample is based on the [Self-Host](../../../../docs/framework/wcf/samples/self-host.md) sample.</span></span> <span data-ttu-id="192cc-105">Konfigurační soubory klienta a služby jsou stejné jako [hostování na vlastním](../../../../docs/framework/wcf/samples/self-host.md) ukázka.</span><span class="sxs-lookup"><span data-stu-id="192cc-105">The service and client configuration files are the same as that of the [Self-Host](../../../../docs/framework/wcf/samples/self-host.md) sample.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="192cc-106">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="192cc-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="192cc-107">Kódu služby se změnilo tak, aby `Add` metoda služby zosobňuje volající pomocí <xref:System.ServiceModel.OperationBehaviorAttribute> jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="192cc-107">The service code has been modified such that the `Add` method on the service impersonates the caller using the <xref:System.ServiceModel.OperationBehaviorAttribute> as shown in the following sample code.</span></span>  
  
```  
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
  
 <span data-ttu-id="192cc-108">V důsledku toho je přepnuta kontext zabezpečení provádění vlákna zosobnit volající před vstupem `Add` metoda a vrátili zpět na ukončení metodu.</span><span class="sxs-lookup"><span data-stu-id="192cc-108">As a result, the security context of the executing thread is switched to impersonate the caller before entering the `Add` method and reverted on exiting the method.</span></span>  
  
 <span data-ttu-id="192cc-109">`DisplayIdentityInformation` Metody uvedené v následující vzorový kód je nástroj funkce, která zobrazuje identitu volajícího.</span><span class="sxs-lookup"><span data-stu-id="192cc-109">The `DisplayIdentityInformation` method shown in the following sample code is a utility function that displays the caller's identity.</span></span>  
  
```  
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
  
 <span data-ttu-id="192cc-110">`Subtract` Metoda služby zosobňuje volající pomocí imperativní volání, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="192cc-110">The `Subtract` method on the service impersonates the caller using imperative calls as shown in the following sample code.</span></span>  
  
```  
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
  
 <span data-ttu-id="192cc-111">Všimněte si, že v tomto případě volající není zosobnit celý volání, ale je pouze zosobnit část volání.</span><span class="sxs-lookup"><span data-stu-id="192cc-111">Note that in this case the caller is not impersonated for the entire call but is only impersonated for a portion of the call.</span></span> <span data-ttu-id="192cc-112">Obecně platí zosobnění pro co nejmenší obor je vhodnější zosobnění pro celou operaci.</span><span class="sxs-lookup"><span data-stu-id="192cc-112">In general, impersonating for the smallest scope is preferable to impersonating for the entire operation.</span></span>  
  
 <span data-ttu-id="192cc-113">Jiné metody nezosobňovat volající.</span><span class="sxs-lookup"><span data-stu-id="192cc-113">The other methods do not impersonate the caller.</span></span>  
  
 <span data-ttu-id="192cc-114">Kód klienta se změnila nastavení na úrovni zosobnění <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>.</span><span class="sxs-lookup"><span data-stu-id="192cc-114">The client code has been modified to set the impersonation level to <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>.</span></span> <span data-ttu-id="192cc-115">Klient určuje úroveň zosobnění má být používána služby, pomocí <xref:System.Security.Principal.TokenImpersonationLevel> výčtu.</span><span class="sxs-lookup"><span data-stu-id="192cc-115">The client specifies the impersonation level to be used by the service, by using the <xref:System.Security.Principal.TokenImpersonationLevel> enumeration.</span></span> <span data-ttu-id="192cc-116">Výčet podporuje následující hodnoty: <xref:System.Security.Principal.TokenImpersonationLevel.None>, <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, <xref:System.Security.Principal.TokenImpersonationLevel.Identification>, <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> a <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>.</span><span class="sxs-lookup"><span data-stu-id="192cc-116">The enumeration supports the following values: <xref:System.Security.Principal.TokenImpersonationLevel.None>, <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, <xref:System.Security.Principal.TokenImpersonationLevel.Identification>, <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> and <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>.</span></span> <span data-ttu-id="192cc-117">Chcete-li provést kontrolu přístupu při přístupu k systémového prostředku v místním počítači, který je chráněný pomocí seznamů ACL systému Windows, musí být nastavena úroveň zosobnění <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="192cc-117">To perform an access check when accessing a system resource on the local machine that is protected using Windows ACLs, the impersonation level must be set to <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>, as shown in the following sample code.</span></span>  
  
```  
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
client.ClientCredentials.Windows.AllowedImpersonationLevel = TokenImpersonationLevel.Impersonation;  
```  
  
 <span data-ttu-id="192cc-118">Při spuštění vzorového operaci požadavky a odpovědi se zobrazují v oknech konzoly služby a klienta.</span><span class="sxs-lookup"><span data-stu-id="192cc-118">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="192cc-119">Stisknutím klávesy ENTER v každé okna konzoly vypnout klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="192cc-119">Press ENTER in each console window to shut down the service and client.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="192cc-120">Služba musí buď spustit pod účtem správce nebo účet jeho spuštění ve musí být udělena práva k registraci http://localhost:8000/ServiceModelSamples identifikátor URI s vrstvě protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="192cc-120">The service must either run under an administrative account or the account it runs under must be granted rights to register the http://localhost:8000/ServiceModelSamples URI with the HTTP layer.</span></span> <span data-ttu-id="192cc-121">Tato oprávnění lze udělit nastavením [Namespace rezervace](http://go.microsoft.com/fwlink/?LinkId=95012) pomocí [Httpcfg.exe nástroj](http://go.microsoft.com/fwlink/?LinkId=95010).</span><span class="sxs-lookup"><span data-stu-id="192cc-121">Such rights can be granted by setting up a [Namespace Reservation](http://go.microsoft.com/fwlink/?LinkId=95012) using the [Httpcfg.exe tool](http://go.microsoft.com/fwlink/?LinkId=95010).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="192cc-122">V počítačích se systémem [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], zosobnění je podporováno pouze v případě, že aplikace Host.exe má oprávnění k zosobnění.</span><span class="sxs-lookup"><span data-stu-id="192cc-122">On computers running [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], impersonation is supported only if the Host.exe application has the Impersonation privilege.</span></span> <span data-ttu-id="192cc-123">(Ve výchozím nastavení mají pouze správci toto oprávnění.) Chcete-li přidat toto oprávnění k účtu, jako je služba spuštěná, přejděte na **nástroje pro správu**, otevřete **místní zásady zabezpečení**, otevřete **místní zásady**, klikněte na tlačítko **Přiřazení uživatelských práv**a vyberte **zosobnit klienta po ověření** a dvakrát klikněte na **vlastnosti** přidat uživatele nebo skupinu.</span><span class="sxs-lookup"><span data-stu-id="192cc-123">(By default, only administrators have this permission.) To add this privilege to an account the service is running as, go to **Administrative Tools**, open **Local Security Policy**, open **Local Policies**, click **User Rights Assignment**, and select **Impersonate a Client after Authentication** and double-click **Properties** to add a user or group.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="192cc-124">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="192cc-124">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="192cc-125">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="192cc-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="192cc-126">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="192cc-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="192cc-127">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="192cc-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="192cc-128">K prokázání, že služba zosobňuje volající, spusťte klienta pod jiným účtem než ten, který je služba spuštěná v části.</span><span class="sxs-lookup"><span data-stu-id="192cc-128">To demonstrate that the service impersonates the caller, run the client under a different account than the one the service is running under.</span></span> <span data-ttu-id="192cc-129">Uděláte to tak, že na příkazovém řádku zadejte:</span><span class="sxs-lookup"><span data-stu-id="192cc-129">To do so, at the command prompt, type:</span></span>  
  
    ```  
    runas /user:<machine-name>\<user-name> client.exe  
    ```  
  
     <span data-ttu-id="192cc-130">Zobrazí se výzva k zadání hesla.</span><span class="sxs-lookup"><span data-stu-id="192cc-130">You are then prompted for a password.</span></span> <span data-ttu-id="192cc-131">Zadejte heslo pro účet, který jste zadali dřív.</span><span class="sxs-lookup"><span data-stu-id="192cc-131">Enter the password for the account you previously specified.</span></span>  
  
5.  <span data-ttu-id="192cc-132">Při spuštění klienta si povšimněte identity před a po spuštění s odlišnými pověřeními.</span><span class="sxs-lookup"><span data-stu-id="192cc-132">When you run the client, note the identity before and after running it with different credentials.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="192cc-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="192cc-133">See Also</span></span>
