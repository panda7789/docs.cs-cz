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
# <a name="impersonating-the-client"></a>Zosobnění klienta
Ukázka zosobnění ukazuje, jak zosobnit volající aplikace ve službě tak, aby služba přístup k systémovým prostředkům jménem volajícího.  
  
 Tato ukázka je založena na [ukázku vlastního hostitele.](../../../../docs/framework/wcf/samples/self-host.md) Konfigurační soubory služby a klienta jsou stejné jako u ukázky [vlastního hostitele.](../../../../docs/framework/wcf/samples/self-host.md)  
  
> [!NOTE]
> Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.  
  
 Kód služby byl upraven `Add` tak, že metoda ve službě <xref:System.ServiceModel.OperationBehaviorAttribute> zosobňuje volajícího pomocí jak je znázorněno v následujícím ukázkovém kódu.  
  
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
  
 V důsledku toho kontext zabezpečení vykonávajícího vlákna je přepnut na `Add` zosobnění volajícího před zadáním metody a vrácena při ukončení metody.  
  
 Metoda `DisplayIdentityInformation` zobrazená v následujícím ukázkovém kódu je nástrojová funkce, která zobrazuje identitu volajícího.  
  
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
  
 Metoda `Subtract` ve službě zosobňuje volajícího pomocí imperativní volání, jak je znázorněno v následujícím ukázkovém kódu.  
  
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
  
 Všimněte si, že v tomto případě volající není zosobněn pro celý hovor, ale je pouze zosobněný pro část volání. Obecně platí, že zosobnění pro nejmenší obor je vhodnější než zosobnění pro celou operaci.  
  
 Ostatní metody nezosobňují volajícího.  
  
 Kód klienta byl upraven tak, aby <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>nastavil úroveň zosobnění na . Klient určuje úroveň zosobnění, která má být použita <xref:System.Security.Principal.TokenImpersonationLevel> službou pomocí výčtu. Výčet podporuje následující hodnoty: <xref:System.Security.Principal.TokenImpersonationLevel.None> <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, <xref:System.Security.Principal.TokenImpersonationLevel.Identification> <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> , <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>a . Chcete-li provést kontrolu přístupu při přístupu k systémovému prostředku v místním počítači, který je <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>chráněn pomocí seznamů ACL systému Windows, musí být úroveň zosobnění nastavena na hodnotu , jak je znázorněno v následujícím ukázkovém kódu.  
  
```csharp
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
client.ClientCredentials.Windows.AllowedImpersonationLevel = TokenImpersonationLevel.Impersonation;  
```  
  
 Při spuštění ukázky jsou požadavky na operaci a odpovědi zobrazeny v systému Windows služby i klientské konzole. Stisknutím klávesy ENTER v každém okně konzoly vypněte službu a klienta.  
  
> [!NOTE]
> Služba musí být spuštěna pod účtem správce nebo účet, pod `http://localhost:8000/ServiceModelSamples` kterým je spuštěna, musí mít udělena práva k registraci identifikátoru URI s vrstvou HTTP. Tato práva lze udělit nastavením [rezervace oboru názvů](/windows/win32/http/namespace-reservations-registrations-and-routing) pomocí nástroje [Httpcfg.exe](/windows/win32/http/httpcfg-exe).  
  
> [!NOTE]
> V počítačích se systémem Windows Server 2003 je zosobnění podporováno pouze v případě, že má aplikace Host.exe oprávnění Zosobnění. (Ve výchozím nastavení mají toto oprávnění pouze správci.) Chcete-li přidat toto oprávnění k účtu, který je spuštěn službou, přejděte na **položku Nástroje pro správu**, otevřete **místní zásady**, otevřete **místní zásady**, klepněte na tlačítko **Přiřazení uživatelských práv**a po ověření vyberte **zosobnit klienta** a poklepejte na **položku Vlastnosti** a přidejte uživatele nebo skupinu.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
4. Chcete-li prokázat, že služba zosobňuje volajícího, spusťte klienta pod jiným účtem, než pod kterým je služba spuštěna. Chcete-li tak učinit, zadejte na příkazovém řádku:  
  
    ```console  
    runas /user:<machine-name>\<user-name> client.exe  
    ```  
  
     Poté budete vyzváni k zadání hesla. Zadejte heslo pro dříve zadaný účet.  
  
5. Při spuštění klienta si poznamenejte identitu před a po spuštění s různými pověřeními.  
