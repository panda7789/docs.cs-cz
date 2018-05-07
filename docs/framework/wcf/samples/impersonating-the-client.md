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
---
# <a name="impersonating-the-client"></a>Zosobnění klienta
Ukázka zosobnění ukazuje, jak zosobnit volající aplikace ve službě, aby služba přístup jménem volající systémové prostředky.  
  
 Tato ukázka je založena na [hostování na vlastním](../../../../docs/framework/wcf/samples/self-host.md) ukázka. Konfigurační soubory klienta a služby jsou stejné jako [hostování na vlastním](../../../../docs/framework/wcf/samples/self-host.md) ukázka.  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 Kódu služby se změnilo tak, aby `Add` metoda služby zosobňuje volající pomocí <xref:System.ServiceModel.OperationBehaviorAttribute> jak je znázorněno v následujícím ukázkovém kódu.  
  
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
  
 V důsledku toho je přepnuta kontext zabezpečení provádění vlákna zosobnit volající před vstupem `Add` metoda a vrátili zpět na ukončení metodu.  
  
 `DisplayIdentityInformation` Metody uvedené v následující vzorový kód je nástroj funkce, která zobrazuje identitu volajícího.  
  
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
  
 `Subtract` Metoda služby zosobňuje volající pomocí imperativní volání, jak je znázorněno v následujícím ukázkovém kódu.  
  
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
  
 Všimněte si, že v tomto případě volající není zosobnit celý volání, ale je pouze zosobnit část volání. Obecně platí zosobnění pro co nejmenší obor je vhodnější zosobnění pro celou operaci.  
  
 Jiné metody nezosobňovat volající.  
  
 Kód klienta se změnila nastavení na úrovni zosobnění <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>. Klient určuje úroveň zosobnění má být používána služby, pomocí <xref:System.Security.Principal.TokenImpersonationLevel> výčtu. Výčet podporuje následující hodnoty: <xref:System.Security.Principal.TokenImpersonationLevel.None>, <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, <xref:System.Security.Principal.TokenImpersonationLevel.Identification>, <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> a <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>. Chcete-li provést kontrolu přístupu při přístupu k systémového prostředku v místním počítači, který je chráněný pomocí seznamů ACL systému Windows, musí být nastavena úroveň zosobnění <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>, jak je znázorněno v následujícím ukázkovém kódu.  
  
```  
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
client.ClientCredentials.Windows.AllowedImpersonationLevel = TokenImpersonationLevel.Impersonation;  
```  
  
 Při spuštění vzorového operaci požadavky a odpovědi se zobrazují v oknech konzoly služby a klienta. Stisknutím klávesy ENTER v každé okna konzoly vypnout klienta a služby.  
  
> [!NOTE]
>  Služba musí buď spustit pod účtem správce nebo účet jeho spuštění ve musí být udělena práva k registraci http://localhost:8000/ServiceModelSamples identifikátor URI s vrstvě protokolu HTTP. Tato oprávnění lze udělit nastavením [Namespace rezervace](http://go.microsoft.com/fwlink/?LinkId=95012) pomocí [Httpcfg.exe nástroj](http://go.microsoft.com/fwlink/?LinkId=95010).  
  
> [!NOTE]
>  V počítačích se systémem [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], zosobnění je podporováno pouze v případě, že aplikace Host.exe má oprávnění k zosobnění. (Ve výchozím nastavení mají pouze správci toto oprávnění.) Chcete-li přidat toto oprávnění k účtu, jako je služba spuštěná, přejděte na **nástroje pro správu**, otevřete **místní zásady zabezpečení**, otevřete **místní zásady**, klikněte na tlačítko **Přiřazení uživatelských práv**a vyberte **zosobnit klienta po ověření** a dvakrát klikněte na **vlastnosti** přidat uživatele nebo skupinu.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
4.  K prokázání, že služba zosobňuje volající, spusťte klienta pod jiným účtem než ten, který je služba spuštěná v části. Uděláte to tak, že na příkazovém řádku zadejte:  
  
    ```  
    runas /user:<machine-name>\<user-name> client.exe  
    ```  
  
     Zobrazí se výzva k zadání hesla. Zadejte heslo pro účet, který jste zadali dřív.  
  
5.  Při spuštění klienta si povšimněte identity před a po spuštění s odlišnými pověřeními.  
  
## <a name="see-also"></a>Viz také
