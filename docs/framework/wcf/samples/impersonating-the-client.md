---
title: Zosobnění klienta
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, impersonation sample
- Impersonating the Client Sample [Windows Communication Foundation]
- impersonation, Windows Communication Foundation sample
ms.assetid: 8bd974e1-90db-4152-95a3-1d4b1a7734f8
ms.openlocfilehash: e9e85729b10d1c992a22f6c0bea65dfd1e21e7e4
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742550"
---
# <a name="impersonating-the-client"></a>Zosobnění klienta
Ukázka zosobnění ukazuje, jak zosobnit volající aplikaci ve službě, aby služba mohla přistupovat k systémovým prostředkům jménem volajícího.  
  
 Tato ukázka je založená na ukázce [samostatného hostitele](../../../../docs/framework/wcf/samples/self-host.md) . Konfigurační soubory služby a klienta jsou stejné jako v ukázce [samostatného hostitele](../../../../docs/framework/wcf/samples/self-host.md) .  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
 Kód služby byl změněn tak, aby metoda `Add` ve službě zosobňuje volajícího pomocí <xref:System.ServiceModel.OperationBehaviorAttribute>, jak je znázorněno v následujícím ukázkovém kódu.  
  
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
  
 V důsledku toho je kontext zabezpečení vykonávajícího vlákna přepnut na zosobnění volajícího před vstupem do metody `Add` a při ukončení metody byl vrácen zpět.  
  
 Metoda `DisplayIdentityInformation` zobrazená v následujícím ukázkovém kódu je funkce nástroje, která zobrazuje identitu volajícího.  
  
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
  
 Metoda `Subtract` ve službě zosobňuje volajícího pomocí imperativních volání, jak je znázorněno v následujícím ukázkovém kódu.  
  
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
  
 Všimněte si, že v tomto případě volající není zosobněn pro celé volání, ale je zosobněna pouze pro část volání. Obecně platí, že zosobnění pro nejmenší rozsah je vhodnější pro zosobnění pro celou operaci.  
  
 Jiné metody nezosobňuje volajícího.  
  
 Kód klienta byl upraven, aby bylo možné nastavit úroveň zosobnění na <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>. Klient Určuje úroveň zosobnění, kterou bude služba používat, pomocí výčtu <xref:System.Security.Principal.TokenImpersonationLevel>. Výčet podporuje následující hodnoty: <xref:System.Security.Principal.TokenImpersonationLevel.None>, <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, <xref:System.Security.Principal.TokenImpersonationLevel.Identification>, <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> a <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>. Chcete-li provést kontrolu přístupu při přístupu k systémovému prostředku v místním počítači, který je chráněn pomocí seznamů řízení přístupu systému Windows, musí být úroveň zosobnění nastavena na <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>, jak je znázorněno v následujícím ukázkovém kódu.  
  
```csharp
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
client.ClientCredentials.Windows.AllowedImpersonationLevel = TokenImpersonationLevel.Impersonation;  
```  
  
 Při spuštění ukázky se požadavky na operace a odpovědi zobrazí v oknech služba i klientská konzola. V každém okně konzoly stiskněte klávesu ENTER a ukončete službu a klienta.  
  
> [!NOTE]
> Služba musí běžet buď pod účtem správce, nebo účtem, ve kterém je spuštěný, musí mít udělena práva k registraci identifikátoru URI `http://localhost:8000/ServiceModelSamples` pomocí vrstvy HTTP. Taková práva je možné udělit nastavením [rezervace oboru názvů](/windows/win32/http/namespace-reservations-registrations-and-routing) pomocí [nástroje HttpCfg. exe](/windows/win32/http/httpcfg-exe).  
  
> [!NOTE]
> V počítačích se systémem Windows Server 2003 se zosobnění podporuje pouze v případě, že má aplikace Host. exe oprávnění k zosobnění. (Ve výchozím nastavení mají toto oprávnění pouze správci.) Pokud chcete toto oprávnění přidat k účtu, ve kterém je služba spuštěná, přejděte do části **Nástroje pro správu**, otevřete **místní zásady zabezpečení**, otevřete **místní zásady**, klikněte na **přiřazení uživatelských práv**a vyberte možnost **zosobnit klienta po ověření** a dvakrát klikněte na **vlastnosti** a přidejte uživatele nebo skupinu.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
4. Chcete-li předvést, že služba zosobňuje volajícího, spusťte klienta pod jiným účtem, než je služba spuštěná. Uděláte to tak, že na příkazovém řádku zadáte:  
  
    ```console  
    runas /user:<machine-name>\<user-name> client.exe  
    ```  
  
     Pak se zobrazí výzva k zadání hesla. Zadejte heslo pro účet, který jste zadali dříve.  
  
5. Když spustíte klienta, poznamenejte si identitu před a po spuštění s jinými přihlašovacími údaji.  
