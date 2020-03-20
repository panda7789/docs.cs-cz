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
# <a name="how-to-run-partially-trusted-code-in-a-sandbox"></a>Postupy: Spuštění částečně důvěryhodného kódu v izolovaném prostoru
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Sandboxing je praxe spouštění kódu v prostředí s omezeným zabezpečením, což omezuje přístupová oprávnění udělená kódu. Máte-li například spravovanou knihovnu ze zdroje, kterému zcela nedůvěřujete, neměli byste ji spouštět jako plně důvěryhodnou. Místo toho byste měli umístit kód do izolovaného prostoru, který omezuje jeho oprávnění <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> na ty, které očekáváte, že bude potřebovat (například oprávnění).  
  
 Sandboxing můžete také použít k testování kódu, který budete distribuovat, který bude spuštěn v částečně důvěryhodných prostředích.  
  
 A <xref:System.AppDomain> je efektivní způsob, jak poskytnout izolovaného prostoru pro spravované aplikace. Aplikační domény, které se používají pro spuštění částečně důvěryhodného kódu, mají <xref:System.AppDomain>oprávnění, která definují chráněné prostředky, které jsou k dispozici při spuštění v rámci tohoto . Kód, který <xref:System.AppDomain> běží uvnitř je vázán <xref:System.AppDomain> oprávnění mizená a je povolen přístup pouze k zadaným prostředkům. Obsahuje <xref:System.AppDomain> také <xref:System.Security.Policy.StrongName> pole, které se používá k identifikaci sestavení, které mají být načteny jako plně důvěryhodné. To umožňuje <xref:System.AppDomain> autorovi domény s novou sandboxovou součástí, která umožňuje plnou důvěryhodnost konkrétních pomocných sestavení. Další možností pro načítání sestavení jako plně důvěryhodné je umístit je do globální mezipaměti sestavení; to však načte sestavení jako plně důvěryhodná ve všech aplikačních doménách vytvořených v tomto počítači. Seznam silných názvů podporuje<xref:System.AppDomain> rozhodnutí, které poskytuje restriktivnější určení.  
  
 Přetížení <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> metody můžete použít k určení sady oprávnění pro aplikace, které běží v izolovaném prostoru. Toto přetížení umožňuje zadat přesnou úroveň zabezpečení přístupu kódu, které chcete. Sestavení, které jsou <xref:System.AppDomain> načteny do pomocí tohoto přetížení může mít buď zadanou sadu grantů pouze, nebo může být plně důvěryhodný. Sestavení je udělen úplný vztah důvěryhodnosti, pokud je `fullTrustAssemblies` v <xref:System.Security.Policy.StrongName>globální mezipaměti sestavení nebo je uvedeno v parametru () pole. Do seznamu by měla být přidána `fullTrustAssemblies` pouze sestavení, o kterých je známo, že jsou plně důvěryhodná.  
  
 Přetížení má následující podpis:  
  
```csharp
AppDomain.CreateDomain( string friendlyName,  
                        Evidence securityInfo,  
                        AppDomainSetup info,  
                        PermissionSet grantSet,  
                        params StrongName[] fullTrustAssemblies);  
```  
  
 Parametry pro <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> přetížení metody určují název <xref:System.AppDomain>, důkaz <xref:System.AppDomain>pro <xref:System.AppDomainSetup> , objekt, který identifikuje základnu aplikace pro izolovaného prostoru, sadu oprávnění k použití a silné názvy pro plně důvěryhodná sestavení.  
  
 Z bezpečnostních důvodů by základ `info` aplikace zadaný v parametru neměl být základem aplikace pro hostitelskou aplikaci.  
  
 Pro `grantSet` parametr můžete zadat buď sadu oprávnění, kterou jste explicitně vytvořili, nebo standardní sadu oprávnění vytvořenou <xref:System.Security.SecurityManager.GetStandardSandbox%2A> metodou.  
  
 Na <xref:System.AppDomain> rozdíl od většiny <xref:System.AppDomain> zatížení důkazy pro (který je k dispozici `securityInfo` parametr) se nepoužívá k určení sady grantů pro částečně důvěryhodná sestavení. Místo toho je nezávisle určen `grantSet` parametrem. Důkazy však mohou být použity pro jiné účely, jako je například určení rozsahu izolované úložiště.  
  
### <a name="to-run-an-application-in-a-sandbox"></a>Spuštění aplikace v izolovaném prostoru  
  
1. Vytvořte sadu oprávnění, která má být udělena nedůvěryhodné aplikaci. Minimální oprávnění, které <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> můžete udělit, je oprávnění. Můžete také udělit další oprávnění, o kterých si myslíte, že mohou být pro nedůvěryhodný kód bezpečná. například <xref:System.Security.Permissions.IsolatedStorageFilePermission>. Následující kód vytvoří novou sadu <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> oprávnění pouze s oprávněním.  
  
    ```csharp
    PermissionSet permSet = new PermissionSet(PermissionState.None);  
    permSet.AddPermission(new SecurityPermission(SecurityPermissionFlag.Execution));  
    ```  
  
     Případně můžete použít existující sadu pojmenovaných oprávnění, například Internet.  
  
    ```csharp
    Evidence ev = new Evidence();  
    ev.AddHostEvidence(new Zone(SecurityZone.Internet));  
    PermissionSet internetPS = SecurityManager.GetStandardSandbox(ev);  
    ```  
  
     Metoda <xref:System.Security.SecurityManager.GetStandardSandbox%2A> vrátí sadu `Internet` oprávnění nebo `LocalIntranet` sadu oprávnění v závislosti na zóně v důkazech. <xref:System.Security.SecurityManager.GetStandardSandbox%2A>také vytvoří oprávnění identity pro některé objekty legitimace předané jako odkazy.  
  
2. Podepište sestavení, které obsahuje `Sandboxer` třídu hostování (pojmenovanou v tomto příkladu), která volá nedůvěryhodný kód. Přidejte <xref:System.Security.Policy.StrongName> slouží k podepsání <xref:System.Security.Policy.StrongName> sestavení `fullTrustAssemblies` do pole <xref:System.AppDomain.CreateDomain%2A> parametr volání. Hostitelská třída musí být spuštěna jako plně důvěryhodná, aby bylo možné spustit kód částečné důvěryhodnosti nebo nabízet služby pro aplikaci s částečnou důvěryhodností. To je, jak <xref:System.Security.Policy.StrongName> si přečíst sestavení:  
  
    ```csharp
    StrongName fullTrustAssembly = typeof(Sandboxer).Assembly.Evidence.GetHostEvidence<StrongName>();  
    ```  
  
     Sestavení rozhraní .NET Framework, jako jsou mscorlib a System.dll, nemusí být přidána do seznamu úplných vztahů důvěryhodnosti, protože jsou načtena jako plně důvěryhodná z globální mezipaměti sestavení.  
  
3. Inicializovat <xref:System.AppDomainSetup> parametr <xref:System.AppDomain.CreateDomain%2A> metody. Pomocí tohoto parametru můžete řídit mnoho nastavení <xref:System.AppDomain>nového . Vlastnost <xref:System.AppDomainSetup.ApplicationBase%2A> je důležité nastavení a měla by <xref:System.AppDomainSetup.ApplicationBase%2A> se <xref:System.AppDomain> lišit od vlastnosti hostitelské aplikace. Pokud <xref:System.AppDomainSetup.ApplicationBase%2A> jsou nastavení stejná, aplikace s částečnou důvěryhodností může získat hostitelskou aplikaci k načtení (jako plně důvěryhodné) výjimku, kterou definuje, a tím ji zneužít. To je další důvod, proč se nedoporučuje catch (výjimka). Nastavení základu aplikace hostitele odlišně od základu aplikace aplikace v izolovaném prostoru zmírňuje riziko zneužití.  
  
    ```csharp
    AppDomainSetup adSetup = new AppDomainSetup();  
    adSetup.ApplicationBase = Path.GetFullPath(pathToUntrusted);  
    ```  
  
4. Volání <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> přetížení metody k vytvoření domény aplikace pomocí parametrů, které jsme zadali.  
  
     Podpis pro tuto metodu je:  
  
    ```csharp
    public static AppDomain CreateDomain(string friendlyName,
        Evidence securityInfo, AppDomainSetup info, PermissionSet grantSet,
        params StrongName[] fullTrustAssemblies)  
    ```  
  
     Další informace:  
  
    - Toto je pouze <xref:System.AppDomain.CreateDomain%2A> přetížení metody, <xref:System.Security.PermissionSet> která trvá jako parametr a tedy pouze přetížení, které umožňuje načíst aplikaci v nastavení částečné důvěryhodnosti.  
  
    - Parametr `evidence` se nepoužívá k výpočtu sady oprávnění. používá se pro identifikaci jinými funkcemi rozhraní .NET Framework.  
  
    - Nastavení <xref:System.AppDomainSetup.ApplicationBase%2A> vlastnosti `info` parametru je pro toto přetížení povinné.  
  
    - Parametr `fullTrustAssemblies` má `params` klíčové slovo, což znamená, že <xref:System.Security.Policy.StrongName> není nutné vytvořit pole. Předávání 0, 1 nebo více silných názvů jako parametry je povoleno.  
  
    - Kód pro vytvoření domény aplikace je:  
  
    ```csharp
    AppDomain newDomain = AppDomain.CreateDomain("Sandbox", null, adSetup, permSet, fullTrustAssembly);  
    ```  
  
5. Načtěte kód do <xref:System.AppDomain> izolovaného prostoru, který jste vytvořili. To lze provést dvěma způsoby:  
  
    - Volání <xref:System.AppDomain.ExecuteAssembly%2A> metody pro sestavení.  
  
    - Pomocí <xref:System.Activator.CreateInstanceFrom%2A> metody vytvořte instanci třídy <xref:System.MarshalByRefObject> odvozené <xref:System.AppDomain>z nové .  
  
     Druhá metoda je vhodnější, protože usnadňuje předávání parametrů do <xref:System.AppDomain> nové instance. Metoda <xref:System.Activator.CreateInstanceFrom%2A> poskytuje dvě důležité funkce:  
  
    - Můžete použít základ kódu, který odkazuje na umístění, které neobsahuje vaše sestavení.  
  
    - Vytvoření můžete provést v <xref:System.Security.CodeAccessPermission.Assert%2A> rámci pro<xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType>plnou důvěryhodnost ( ), která umožňuje vytvořit instanci kritické třídy. (K tomu dochází vždy, když vaše sestava nemá žádné označení průhlednosti a je načtena jako plně důvěryhodná.) Proto musíte být opatrní vytvořit pouze kód, kterému důvěřujete s touto funkcí a doporučujeme vytvořit pouze instance plně důvěryhodné třídy v nové doméně aplikace.  
  
    ```csharp
    ObjectHandle handle = Activator.CreateInstanceFrom(  
    newDomain, typeof(Sandboxer).Assembly.ManifestModule.FullyQualifiedName,  
           typeof(Sandboxer).FullName );  
    ```  
  
     Všimněte si, že k vytvoření instance třídy v nové doméně, třída musí rozšířit třídu <xref:System.MarshalByRefObject>  
  
    ```csharp
    class Sandboxer:MarshalByRefObject  
    ```  
  
6. Rozbalte novou instanci domény do odkazu v této doméně. Tento odkaz se používá ke spuštění nedůvěryhodného kódu.  
  
    ```csharp
    Sandboxer newDomainInstance = (Sandboxer) handle.Unwrap();  
    ```  
  
7. Volání `ExecuteUntrustedCode` metody v instanci třídy, kterou `Sandboxer` jste právě vytvořili.  
  
    ```csharp
    newDomainInstance.ExecuteUntrustedCode(untrustedAssembly, untrustedClass, entryPoint, parameters);  
    ```  
  
     Toto volání je provedeno v doméně aplikace v izolovaném prostoru, která má omezená oprávnění.  
  
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
  
     <xref:System.Reflection>se používá k získání popisovače metody v částečně důvěryhodném sestavení. Popisovač lze spustit kód bezpečným způsobem s minimálními oprávněními.  
  
     V předchozím kódu si <xref:System.Security.PermissionSet.Assert%2A> před tiskem aplikace všimněte plné důvěryhodnosti <xref:System.Security.SecurityException>oprávnění pro úplnou důvěryhodnost.  
  
    ```csharp
    new PermissionSet(PermissionState.Unrestricted).Assert()  
    ```  
  
     Plně důvěryhodné assert se používá k získání <xref:System.Security.SecurityException>rozšířené informace z . Bez <xref:System.Security.PermissionSet.Assert%2A>, <xref:System.Security.SecurityException.ToString%2A> metoda <xref:System.Security.SecurityException> zjistíte, že je částečně důvěryhodný kód v zásobníku a omezí vrácené informace. To by mohlo způsobit problémy se zabezpečením, pokud kód částečné důvěryhodnosti <xref:System.Security.Permissions.UIPermission>může číst tyto informace, ale riziko je zmírněno tím, že neuděluje . Full-trust assert by měl být používán střídmě a pouze v případě, že jste si jisti, že nepovolujete kód částečné důvěryhodnosti, aby se zvýšil na úplný vztah důvěryhodnosti. Zpravidla nevolejte kód, kterému nedůvěřujete ve stejné funkci, a poté, co jste zavolali assert pro úplný vztah důvěryhodnosti. Je vhodné vždy vrátit assert po dokončení jeho použití.  
  
## <a name="example"></a>Příklad  
 Následující příklad implementuje postup v předchozí části. V příkladu projekt `Sandboxer` s názvem v řešení sady `UntrustedCode`Visual Studio také `UntrustedClass`obsahuje projekt s názvem , který implementuje třídu . Tento scénář předpokládá, že jste stáhli sestavení knihovny obsahující `true` metodu, která se očekává, že se vrátí nebo `false` označuje, zda je zadaným číslem Fibonacciho číslo. Místo toho se metoda pokusí číst soubor z počítače. Následující příklad ukazuje nedůvěryhodný kód.  
  
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
  
 Následující příklad ukazuje `Sandboxer` kód aplikace, který spustí nedůvěryhodný kód.  
  
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
  
## <a name="see-also"></a>Viz také

- [Pokyny pro zabezpečené kódování](../../standard/security/secure-coding-guidelines.md)
