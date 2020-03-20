---
title: Zosobnění klienta
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, impersonation sample
- Impersonating the Client Sample [Windows Communication Foundation]
- impersonation, Windows Communication Foundation sample
ms.assetid: 8bd974e1-90db-4152-95a3-1d4b1a7734f8
ms.openlocfilehash: 10a8d243b3f053879f183864e955d9260c07865b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183614"
---
# <a name="impersonating-the-client"></a><span data-ttu-id="28296-102">Zosobnění klienta</span><span class="sxs-lookup"><span data-stu-id="28296-102">Impersonating the Client</span></span>
<span data-ttu-id="28296-103">Ukázka zosobnění ukazuje, jak zosobnit volající aplikace ve službě tak, aby služba přístup k systémovým prostředkům jménem volajícího.</span><span class="sxs-lookup"><span data-stu-id="28296-103">The Impersonation sample demonstrates how to impersonate the caller application at the service so that the service can access system resources on behalf of the caller.</span></span>  
  
 <span data-ttu-id="28296-104">Tato ukázka je založena na [ukázku vlastního hostitele.](../../../../docs/framework/wcf/samples/self-host.md)</span><span class="sxs-lookup"><span data-stu-id="28296-104">This sample is based on the [Self-Host](../../../../docs/framework/wcf/samples/self-host.md) sample.</span></span> <span data-ttu-id="28296-105">Konfigurační soubory služby a klienta jsou stejné jako u ukázky [vlastního hostitele.](../../../../docs/framework/wcf/samples/self-host.md)</span><span class="sxs-lookup"><span data-stu-id="28296-105">The service and client configuration files are the same as that of the [Self-Host](../../../../docs/framework/wcf/samples/self-host.md) sample.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="28296-106">Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="28296-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="28296-107">Kód služby byl upraven `Add` tak, že metoda ve službě <xref:System.ServiceModel.OperationBehaviorAttribute> zosobňuje volajícího pomocí jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="28296-107">The service code has been modified such that the `Add` method on the service impersonates the caller using the <xref:System.ServiceModel.OperationBehaviorAttribute> as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="28296-108">V důsledku toho kontext zabezpečení vykonávajícího vlákna je přepnut na `Add` zosobnění volajícího před zadáním metody a vrácena při ukončení metody.</span><span class="sxs-lookup"><span data-stu-id="28296-108">As a result, the security context of the executing thread is switched to impersonate the caller before entering the `Add` method and reverted on exiting the method.</span></span>  
  
 <span data-ttu-id="28296-109">Metoda `DisplayIdentityInformation` zobrazená v následujícím ukázkovém kódu je nástrojová funkce, která zobrazuje identitu volajícího.</span><span class="sxs-lookup"><span data-stu-id="28296-109">The `DisplayIdentityInformation` method shown in the following sample code is a utility function that displays the caller's identity.</span></span>  
  
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
  
 <span data-ttu-id="28296-110">Metoda `Subtract` ve službě zosobňuje volajícího pomocí imperativní volání, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="28296-110">The `Subtract` method on the service impersonates the caller using imperative calls as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="28296-111">Všimněte si, že v tomto případě volající není zosobněn pro celý hovor, ale je pouze zosobněný pro část volání.</span><span class="sxs-lookup"><span data-stu-id="28296-111">Note that in this case the caller is not impersonated for the entire call but is only impersonated for a portion of the call.</span></span> <span data-ttu-id="28296-112">Obecně platí, že zosobnění pro nejmenší obor je vhodnější než zosobnění pro celou operaci.</span><span class="sxs-lookup"><span data-stu-id="28296-112">In general, impersonating for the smallest scope is preferable to impersonating for the entire operation.</span></span>  
  
 <span data-ttu-id="28296-113">Ostatní metody nezosobňují volajícího.</span><span class="sxs-lookup"><span data-stu-id="28296-113">The other methods do not impersonate the caller.</span></span>  
  
 <span data-ttu-id="28296-114">Kód klienta byl upraven tak, aby <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>nastavil úroveň zosobnění na .</span><span class="sxs-lookup"><span data-stu-id="28296-114">The client code has been modified to set the impersonation level to <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>.</span></span> <span data-ttu-id="28296-115">Klient určuje úroveň zosobnění, která má být použita <xref:System.Security.Principal.TokenImpersonationLevel> službou pomocí výčtu.</span><span class="sxs-lookup"><span data-stu-id="28296-115">The client specifies the impersonation level to be used by the service, by using the <xref:System.Security.Principal.TokenImpersonationLevel> enumeration.</span></span> <span data-ttu-id="28296-116">Výčet podporuje následující hodnoty: <xref:System.Security.Principal.TokenImpersonationLevel.None> <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, <xref:System.Security.Principal.TokenImpersonationLevel.Identification> <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> , <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>a .</span><span class="sxs-lookup"><span data-stu-id="28296-116">The enumeration supports the following values: <xref:System.Security.Principal.TokenImpersonationLevel.None>, <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, <xref:System.Security.Principal.TokenImpersonationLevel.Identification>, <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> and <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>.</span></span> <span data-ttu-id="28296-117">Chcete-li provést kontrolu přístupu při přístupu k systémovému prostředku v místním počítači, který je <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>chráněn pomocí seznamů ACL systému Windows, musí být úroveň zosobnění nastavena na hodnotu , jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="28296-117">To perform an access check when accessing a system resource on the local machine that is protected using Windows ACLs, the impersonation level must be set to <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>, as shown in the following sample code.</span></span>  
  
```csharp
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
client.ClientCredentials.Windows.AllowedImpersonationLevel = TokenImpersonationLevel.Impersonation;  
```  
  
 <span data-ttu-id="28296-118">Při spuštění ukázky jsou požadavky na operaci a odpovědi zobrazeny v systému Windows služby i klientské konzole.</span><span class="sxs-lookup"><span data-stu-id="28296-118">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="28296-119">Stisknutím klávesy ENTER v každém okně konzoly vypněte službu a klienta.</span><span class="sxs-lookup"><span data-stu-id="28296-119">Press ENTER in each console window to shut down the service and client.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="28296-120">Služba musí být spuštěna pod účtem správce nebo účet, pod `http://localhost:8000/ServiceModelSamples` kterým je spuštěna, musí mít udělena práva k registraci identifikátoru URI s vrstvou HTTP.</span><span class="sxs-lookup"><span data-stu-id="28296-120">The service must either run under an administrative account or the account it runs under must be granted rights to register the `http://localhost:8000/ServiceModelSamples` URI with the HTTP layer.</span></span> <span data-ttu-id="28296-121">Tato práva lze udělit nastavením [rezervace oboru názvů](/windows/win32/http/namespace-reservations-registrations-and-routing) pomocí nástroje [Httpcfg.exe](/windows/win32/http/httpcfg-exe).</span><span class="sxs-lookup"><span data-stu-id="28296-121">Such rights can be granted by setting up a [Namespace Reservation](/windows/win32/http/namespace-reservations-registrations-and-routing) using the [Httpcfg.exe tool](/windows/win32/http/httpcfg-exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="28296-122">V počítačích se systémem Windows Server 2003 je zosobnění podporováno pouze v případě, že má aplikace Host.exe oprávnění Zosobnění.</span><span class="sxs-lookup"><span data-stu-id="28296-122">On computers running Windows Server 2003, impersonation is supported only if the Host.exe application has the Impersonation privilege.</span></span> <span data-ttu-id="28296-123">(Ve výchozím nastavení mají toto oprávnění pouze správci.) Chcete-li přidat toto oprávnění k účtu, který je spuštěn službou, přejděte na **položku Nástroje pro správu**, otevřete **místní zásady**, otevřete **místní zásady**, klepněte na tlačítko **Přiřazení uživatelských práv**a po ověření vyberte **zosobnit klienta** a poklepejte na **položku Vlastnosti** a přidejte uživatele nebo skupinu.</span><span class="sxs-lookup"><span data-stu-id="28296-123">(By default, only administrators have this permission.) To add this privilege to an account the service is running as, go to **Administrative Tools**, open **Local Security Policy**, open **Local Policies**, click **User Rights Assignment**, and select **Impersonate a Client after Authentication** and double-click **Properties** to add a user or group.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="28296-124">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="28296-124">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="28296-125">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="28296-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="28296-126">Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="28296-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="28296-127">Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="28296-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
4. <span data-ttu-id="28296-128">Chcete-li prokázat, že služba zosobňuje volajícího, spusťte klienta pod jiným účtem, než pod kterým je služba spuštěna.</span><span class="sxs-lookup"><span data-stu-id="28296-128">To demonstrate that the service impersonates the caller, run the client under a different account than the one the service is running under.</span></span> <span data-ttu-id="28296-129">Chcete-li tak učinit, zadejte na příkazovém řádku:</span><span class="sxs-lookup"><span data-stu-id="28296-129">To do so, at the command prompt, type:</span></span>  
  
    ```console  
    runas /user:<machine-name>\<user-name> client.exe  
    ```  
  
     <span data-ttu-id="28296-130">Poté budete vyzváni k zadání hesla.</span><span class="sxs-lookup"><span data-stu-id="28296-130">You are then prompted for a password.</span></span> <span data-ttu-id="28296-131">Zadejte heslo pro dříve zadaný účet.</span><span class="sxs-lookup"><span data-stu-id="28296-131">Enter the password for the account you previously specified.</span></span>  
  
5. <span data-ttu-id="28296-132">Při spuštění klienta si poznamenejte identitu před a po spuštění s různými pověřeními.</span><span class="sxs-lookup"><span data-stu-id="28296-132">When you run the client, note the identity before and after running it with different credentials.</span></span>  
