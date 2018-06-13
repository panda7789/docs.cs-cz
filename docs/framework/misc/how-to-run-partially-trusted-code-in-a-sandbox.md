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
# <a name="how-to-run-partially-trusted-code-in-a-sandbox"></a>Postupy: Spuštění částečně důvěryhodného kódu v izolovaném prostoru
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Sandboxing je postup spuštění kódu v prostředí s omezeným přístupem, což omezí přístup oprávnění udělená kód. Například pokud máte spravovanou knihovnu ze zdroje, kterému nedůvěřujete úplně, nespouštějte ji jako plně důvěryhodná. Místo toho byste měli umístit kód do izolovaného prostoru, který omezuje její oprávnění na ty, které očekáváte potřebovat (například <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> oprávnění).  
  
 Sandboxing můžete také použít k testování kódu, které budete distribuovat, který se spustí v prostředí částečně důvěryhodné.  
  
 <xref:System.AppDomain> Je účinný způsob poskytování izolovaném prostoru pro spravované aplikace. Aplikační domény, které se používají pro spuštění částečně důvěryhodného kódu mají oprávnění definující k chráněným prostředkům, které jsou k dispozici při spuštění v rámci které <xref:System.AppDomain>. Kód, který běží v rámci <xref:System.AppDomain> je svázaná s oprávnění spojená s <xref:System.AppDomain> a je povolen přístup pouze zadané prostředky. <xref:System.AppDomain> Také zahrnuje <xref:System.Security.Policy.StrongName> pole, které se používá k identifikaci sestavení, které mají být načteny jako plně důvěryhodná. To umožňuje Tvůrce <xref:System.AppDomain> spustit novou doménu v izolovaném prostoru, která umožňuje konkrétní podpůrné sestavení být plně důvěryhodné. Další možností pro načtení sestavení jako plně důvěryhodné je umístit do globální mezipaměti sestavení; ale, který načte sestavení jako plně důvěryhodný ve všech doménách aplikací vytvořených v tomto počítači. Seznam silných názvů podporujících za-<xref:System.AppDomain> rozhodnutí, která poskytuje více omezující stanovení.  
  
 Můžete použít <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> přetížení metody k zadání oprávnění nastavená pro aplikace, které běží v izolovaném prostoru. Toto přetížení umožňuje určit přesnou úroveň zabezpečení přístupu kódu, které chcete. Sestavení, která jsou načtena do <xref:System.AppDomain> pomocí tohoto přetížení, mohou mít buď zadaný udělit pouze nastavena, nebo může být plně důvěryhodná. Sestavení jsou udělena úplný vztah důvěryhodnosti, pokud je v globální mezipaměti sestavení nebo uvedené v `fullTrustAssemblies` ( <xref:System.Security.Policy.StrongName>) parametr pole. Pouze sestavení, které jsou známé jako plně důvěryhodný pro by měla být přidány do `fullTrustAssemblies` seznamu.  
  
 Přetížení má následující podpis:  
  
```  
AppDomain.CreateDomain( string friendlyName,  
                        Evidence securityInfo,  
                        AppDomainSetup info,  
                        PermissionSet grantSet,  
                        params StrongName[] fullTrustAssemblies);  
```  
  
 Parametry <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> přetížení metody zadejte název <xref:System.AppDomain>, důkaz pro <xref:System.AppDomain>, <xref:System.AppDomainSetup> objekt, který identifikuje základní aplikace pro izolovaný prostor, používat sadu oprávnění a silné názvy pro plně důvěryhodný pro sestavení.  
  
 Z bezpečnostních důvodů základní aplikace zadané v `info` parametr nesmí být základ aplikace pro hostitelskou aplikaci.  
  
 Pro `grantSet` parametr, můžete zadat sadu oprávnění, kterou jste vytvořili explicitně nebo standardní oprávnění, vytvořená <xref:System.Security.SecurityManager.GetStandardSandbox%2A> metoda.  
  
 Na rozdíl od většiny <xref:System.AppDomain> načte, důkaz pro <xref:System.AppDomain> (poskytnutá `securityInfo` parametr) neslouží k určení grant nastavit pro částečně důvěryhodné sestavení. Místo toho je nezávisle určena podle `grantSet` parametr. Důkaz však lze použít k jiným účelům, jako je například určení rozsahu izolovaného úložiště.  
  
### <a name="to-run-an-application-in-a-sandbox"></a>Spuštění aplikace v izolovaném prostoru  
  
1.  Vytvořte sadu udělit oprávnění k nedůvěryhodné aplikaci oprávnění. Minimální oprávnění můžete udělit je <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> oprávnění. Můžete také udělit další oprávnění, které se domníváte, že může být bezpečné pro přístup z nedůvěryhodné kódu; například <xref:System.Security.Permissions.IsolatedStorageFilePermission>. Následující kód vytvoří novou sadu s pouze oprávnění <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> oprávnění.  
  
    ```  
    PermissionSet permSet = new PermissionSet(PermissionState.None);  
    permSet.AddPermission(new SecurityPermission(SecurityPermissionFlag.Execution));  
    ```  
  
     Alternativně můžete použít existující sadu s názvem oprávnění, jako je Internet.  
  
    ```  
    Evidence ev = new Evidence();  
    ev.AddHostEvidence(new Zone(SecurityZone.Internet));  
    PermissionSet internetPS = SecurityManager.GetStandardSandbox(ev);  
    ```  
  
     <xref:System.Security.SecurityManager.GetStandardSandbox%2A> Metoda vrací buď `Internet` sadě oprávnění nebo `LocalIntranet` sady v závislosti na zónu důkazy oprávnění. <xref:System.Security.SecurityManager.GetStandardSandbox%2A> také vytvoří oprávnění identity pro některé objekty důkaz předané jako odkazy.  
  
2.  Podepisování sestavení, které obsahuje hostující třídy (s názvem `Sandboxer` v tomto příkladu), který volá kód nedůvěryhodné. Přidat <xref:System.Security.Policy.StrongName> použité k podepsání sestavení do <xref:System.Security.Policy.StrongName> pole `fullTrustAssemblies` parametr <xref:System.AppDomain.CreateDomain%2A> volání. Hostující třídy musí běžet jako plně důvěryhodná, chcete-li povolit spuštění částečně důvěryhodného kódu nebo nabízí služby do aplikace s částečným vztahem důvěryhodnosti. Toto je, jak číst <xref:System.Security.Policy.StrongName> sestavení:  
  
    ```  
    StrongName fullTrustAssembly = typeof(Sandboxer).Assembly.Evidence.GetHostEvidence<StrongName>();  
    ```  
  
     Sestavení rozhraní .NET framework, jako je například mscorlib a System.dll není nutné přidat do seznamu plné důvěryhodnosti, protože jsou načteny jako plně důvěryhodné z globální mezipaměti sestavení.  
  
3.  Inicializace <xref:System.AppDomainSetup> parametr <xref:System.AppDomain.CreateDomain%2A> metoda. Pomocí tohoto parametru, můžete řídit mnoho nastavení nového <xref:System.AppDomain>. <xref:System.AppDomainSetup.ApplicationBase%2A> Vlastnost je důležité nastavení a měl by být odlišný od <xref:System.AppDomainSetup.ApplicationBase%2A> vlastnost <xref:System.AppDomain> hostitelské aplikace. Pokud <xref:System.AppDomainSetup.ApplicationBase%2A> nastavení jsou stejné, částečně důvěryhodné aplikace můžete získat hostitelskou aplikaci k načtení (jako je plně důvěryhodná) výjimku definuje, tedy zneužít. To je další důvod, proč se nedoporučuje catch (výjimek). Nastavení aplikace základní hostitele odlišně od základní aplikace v izolovaném prostoru aplikace snižuje riziko zneužití.  
  
    ```  
    AppDomainSetup adSetup = new AppDomainSetup();  
    adSetup.ApplicationBase = Path.GetFullPath(pathToUntrusted);  
    ```  
  
4.  Volání <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> přetížení metody pro vytvoření domény aplikace pomocí parametrů jsme určili.  
  
     Podpis pro tuto metodu je:  
  
    ```  
    public static AppDomain CreateDomain(string friendlyName,   
        Evidence securityInfo, AppDomainSetup info, PermissionSet grantSet,   
        params StrongName[] fullTrustAssemblies)  
    ```  
  
     Další informace:  
  
    -   Toto je pouze přetížení <xref:System.AppDomain.CreateDomain%2A> metody, která přijímá <xref:System.Security.PermissionSet> jako parametr a tedy pouze přetížení, které vám umožní načtení aplikace v nastavení částečným vztahem důvěryhodnosti.  
  
    -   `evidence` Parametr se nepoužívá k výpočtu sady oprávnění; slouží k určení dalších funkcí rozhraní .NET Framework.  
  
    -   Nastavení <xref:System.AppDomainSetup.ApplicationBase%2A> vlastnost `info` parametr je povinný pro toto přetížení.  
  
    -   `fullTrustAssemblies` Parametr má `params` – klíčové slovo, což znamená, že není potřeba vytvořit <xref:System.Security.Policy.StrongName> pole. Je povoleno předávání 0, 1 nebo více silných názvů jako parametry.  
  
    -   Kód k vytvoření domény aplikace je:  
  
    ```  
    AppDomain newDomain = AppDomain.CreateDomain("Sandbox", null, adSetup, permSet, fullTrustAssembly);  
    ```  
  
5.  Načtěte kód do sandboxing <xref:System.AppDomain> kterou jste vytvořili. Tento krok můžete provést dvěma způsoby:  
  
    -   Volání <xref:System.AppDomain.ExecuteAssembly%2A> metodu pro sestavení.  
  
    -   Použití <xref:System.Activator.CreateInstanceFrom%2A> metodu pro vytvoření instance třídy odvozené od <xref:System.MarshalByRefObject> v novém <xref:System.AppDomain>.  
  
     Druhá metoda je vhodnější, protože umožňuje jednodušší předat parametry do nového <xref:System.AppDomain> instance. <xref:System.Activator.CreateInstanceFrom%2A> Metoda obsahuje dvě důležité funkce:  
  
    -   Můžete použít základu kódu, který odkazuje na umístění, které neobsahuje vaše sestavení.  
  
    -   Můžete provést vytvoření v rámci <xref:System.Security.CodeAccessPermission.Assert%2A> pro plné důvěryhodnosti (<xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType>), který umožňuje vytvořit instanci kritické třídy. (K tomu dojde vždy, když vaše sestavení nemá žádné označení transparentnosti a je načteno jako plně důvěryhodná.) Proto musíte vytvořit pouze kód, kterému důvěřujete pomocí této funkce pečlivě, a doporučujeme vytvořit pouze instance tříd plně důvěryhodných v nové doméně aplikace.  
  
    ```  
    ObjectHandle handle = Activator.CreateInstanceFrom(  
    newDomain, typeof(Sandboxer).Assembly.ManifestModule.FullyQualifiedName,  
           typeof(Sandboxer).FullName );  
    ```  
  
     Všimněte si, že k vytvoření instance třídy v nové doméně, třída má rozšíření <xref:System.MarshalByRefObject> – třída  
  
    ```  
    class Sandboxer:MarshalByRefObject  
    ```  
  
6.  Rozbalení novou instanci domény do odkaz v této doméně. Tento odkaz se používá k provedení nedůvěryhodný kód.  
  
    ```  
    Sandboxer newDomainInstance = (Sandboxer) handle.Unwrap();  
    ```  
  
7.  Volání `ExecuteUntrustedCode` metoda v instanci systému `Sandboxer` třídy, kterou jste právě vytvořili.  
  
    ```  
    newDomainInstance.ExecuteUntrustedCode(untrustedAssembly, untrustedClass, entryPoint, parameters);  
    ```  
  
     Toto volání se spustí v doméně aplikace v izolovaném prostoru, který má omezená oprávnění.  
  
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
  
     <xref:System.Reflection> slouží k získání popisovače metody v částečně důvěryhodné sestavení. Popisovač slouží ke spouštění kódu bezpečným způsobem s minimálními oprávněními.  
  
     V předchozí kód, Upozorňujeme <xref:System.Security.PermissionSet.Assert%2A> plná oprávnění před tiskem <xref:System.Security.SecurityException>.  
  
    ```  
    new PermissionSet(PermissionState.Unrestricted)).Assert()  
    ```  
  
     Assert plné důvěryhodnosti se používá k získání rozšířených informací z <xref:System.Security.SecurityException>. Bez <xref:System.Security.PermissionSet.Assert%2A>, <xref:System.Security.SecurityException.ToString%2A> metodu <xref:System.Security.SecurityException> zjistí, že je částečně důvěryhodného kódu v zásobníku a omezí vrácené informace. To může způsobit problémy se zabezpečením, pokud částečně důvěryhodný kód mohl přečíst informace, ale riziko zmírnit neudělením <xref:System.Security.Permissions.UIPermission>. Assert plné důvěryhodnosti měli šetřit a jenom v případě, že jste si jisti, že nejsou povolení částečně důvěryhodný kód ke zvýšení oprávnění na úplný vztah důvěryhodnosti. Platí pravidlo upravit kód, který si nejste jisti, ve stejné funkci a po volání požadavku pro úplný vztah důvěryhodnosti. Je dobrým zvykem vždy vrátit assert po dokončení jeho použití.  
  
## <a name="example"></a>Příklad  
 Následující příklad implementuje podle postupu v předchozím oddílu. V příkladu projekt s názvem `Sandboxer` v sadě Visual Studio řešení obsahuje také projekt s názvem `UntrustedCode`, který implementuje třídu `UntrustedClass`. Tento scénář předpokládá, že jste si stáhli sestavení knihovny obsahující metodu, která zpět `true` nebo `false` indikující, zda počet jste zadali, je Fibonacciho číslo. Místo toho metodu pokusí přečíst soubor z vašeho počítače. Následující příklad ukazuje kód nedůvěryhodné.  
  
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
  
 Následující příklad ukazuje `Sandboxer` aplikační kód, který provede nedůvěryhodný kód.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Pokyny pro zabezpečené kódování](../../../docs/standard/security/secure-coding-guidelines.md)
