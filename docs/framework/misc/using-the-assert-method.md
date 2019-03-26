---
title: Použití metody Assert
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- granting permissions, overriding security checks
- code access security, overriding security checks
- overriding security checks
- security [.NET Framework], overriding security checks
- security [.NET Framework], assertions
- asserted permissions
- Assert method
- caller security checks
- permissions [.NET Framework], overriding security checks
- permissions [.NET Framework], assertions
ms.assetid: 1e40f4d3-fb7d-4f19-b334-b6076d469ea9
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5799ab8e827305fca565064a0ae7290c6c19eb01
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2019
ms.locfileid: "58463004"
---
# <a name="using-the-assert-method"></a>Použití metody Assert
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <xref:System.Security.CodeAccessPermission.Assert%2A> představuje metodu, která lze volat pro třídy oprávnění přístupu kódu a na <xref:System.Security.PermissionSet> třídy. Můžete použít **Assert** povolit váš kód (a podřízené volající) k provedení akce, které váš kód má oprávnění k provedení, ale jeho volající nemusí mít oprávnění k provedení. Kontrolní výraz zabezpečení změní normální proces, který modul runtime provádí během kontroly zabezpečení. Pokud uplatňujete oprávnění, informuje systém zabezpečení není ke kontrole volajících váš kód s potvrzením oprávnění.  
  
> [!CAUTION]
>  Kontrolní výrazy používejte opatrně, protože můžete otevřít bezpečnostní díry a narušují modul runtime mechanismus pro vynucení omezení zabezpečení.  
  
 Kontrolní výrazy jsou užitečné v situacích, ve kterých knihovnu volání nespravovaného kódu nebo provede volání, která vyžaduje oprávnění, které samozřejmě nesouvisí s zamýšlené použití knihovny. Například všechen spravovaný kód, který volá nespravovaný kód musí mít **SecurityPermission** s **požadavku na nespravovaný kód** příznak zadán. Kód, který nepochází z místního počítače, jako je kód, který se stáhne z místní intranet, nebudou ve výchozím nastavení udělit toto oprávnění. Proto aby kód, který se stáhne z místního intranetu mohli volání knihovny, která používá nespravovaný kód, musí mít oprávnění s prohlašovanou knihovnou. Kromě toho některé knihovny mohou provádět volání, která jsou viditelná pro volající a vyžadují zvláštní oprávnění.  
  
 Kontrolní výrazy můžete také použít v situacích, kdy váš kód přistupuje k prostředků tak, aby se zcela skryje volajícím. Předpokládejme například, knihovny získává informace z databáze, ale v procesu také čte informace z registru počítače. Protože vývojáři, kteří používají vaše knihovna nemají přístup ke zdroji, nemají žádnou možnost zjistit, že jejich kód vyžaduje **RegistryPermission** Chcete-li použít kód. Pokud se rozhodnete, že není přiměřené nebo nezbytné vyžadují, aby volající kód oprávnění pro přístup k registru, v takovém případě můžete uplatnit oprávnění pro čtení registru. V takovém případě je vhodné pro knihovny uplatnit oprávnění, tak že volající bez **RegistryPermission** můžete použít knihovnu.  
  
 Kontrolní výraz ovlivňuje procházení zásobníku pouze v případě, že s potvrzením oprávnění a oprávnění požadované podřízené volajícím jsou stejného typu a požadované oprávnění je podmnožinou s potvrzením oprávnění. Například, pokud uplatňujete **FileIOPermission** pro čtení všech souborů na jednotce C a podřízený požadavek se provádí **FileIOPermission** ke čtení v C:\Temp kontrolního výrazu by mohla ovlivnit procházení zásobníku; Nicméně pokud požadavek **FileIOPermission** pro zápis k jednotce C kontrolního výrazu by neměl žádný vliv.  
  
 Pokud chcete provést kontrolní výrazy, musí váš kód udělit oprávnění uplatňujete a <xref:System.Security.Permissions.SecurityPermission> , která představuje práva ke kontrolní výrazy. I když může uplatnit oprávnění, které nebylo uděleno kódu, bude kontrolního výrazu bezúčelné vzhledem k tomu, že kontrola zabezpečení by selhat, aby kontrolního výrazu by mohlo způsobit to proběhla úspěšně.  
  
 Následující obrázek znázorňuje, co se stane, když použijete **Assert**. Předpokládejme, že následující tvrzení jsou pravdivá o sestavení A, B, C, E a F a dvě oprávnění, P1 a P1A:  
  
-   P1A představuje oprávnění ke čtení souborů .txt na jednotce C:.  
  
-   P1 představuje oprávnění ke čtení všech souborů na jednotce C:.  
  
-   Jsou P1A i P1 **FileIOPermission** typy a P1A je podmnožinou P1.  
  
-   Sestavení E a F bylo uděleno oprávnění P1A.  
  
-   Sestavení C bylo uděleno oprávnění P1.  
  
-   Sestavení A a B byla udělena oprávnění P1A ani P1.  
  
-   Metoda A je obsažen v sestavení A, metoda B je obsažen v sestavení B a tak dále.  
  
 ![Diagram zobrazující průběh sestavení metody Assert.](./media/using-the-assert-method/assert-method-assemblies.gif)    
  
 V tomto scénáři, metody A volá B, volá B, C, volání jazyka C E, volání E F. Metoda C uplatňuje oprávnění ke čtení souborů na jednotce C (oprávnění P1) a metoda E požaduje oprávnění ke čtení souborů .txt na jednotce C (oprávnění P1A). Při vyžádání v F dochází za běhu, procházení zásobníku se provádí pro kontrolu oprávnění všech volajících F, počínaje E. E bylo uděleno oprávnění P1A tak procházení zásobníku pokračuje ke kontrole oprávnění C, kde je zjištěna kontrolní výraz. Vzhledem k tomu, že požadované oprávnění (P1A) je podmnožinou s potvrzením oprávnění (P1), procházení zásobníku se zastaví a kontrola zabezpečení automaticky proběhne úspěšně. Není důležité, že sestavením A a B nebyla udělena oprávnění P1A. Pomocí uplatňování P1, metoda jazyka C zajišťuje, že jeho volající neměly přístup k prostředku chráněny P1, i v případě, že volající nebylo uděleno oprávnění pro přístup k prostředku.  
  
 Pokud navrhujete knihovny tříd a třídu, má přístup k chráněnému prostředku, by ve většině případů provedete požadavek zabezpečení, že volající třídy mají příslušná oprávnění. Pokud třída pak provede operaci pro které víte, většina volajících nebude mít oprávnění, a pokud jste ochotni nést odpovědnost za umožníte tím tyto volajícím volat kód, lze uplatnit oprávnění pomocí volání **Assert** metodu na objekt oprávnění, která představuje operaci kód provádí. Pomocí **Assert** tímto způsobem umožňuje volajícím obvykle nedosáhli volat váš kód. Proto pokud uplatňujete oprávnění, byste měli provést příslušná bezpečnostní kontroly předem zabránit vaše komponenta před zneužitím.  
  
 Předpokládejme například, že vysoce důvěryhodných knihovna tříd je metoda, která odstraní soubory. Přistupuje k souboru voláním nespravovanou funkci Win32. Volající spustí váš kód **odstranit** metodu předáním názvu souboru, který má být odstraněna, C:\Test.txt. V rámci **odstranit** kódu vytvoří <xref:System.Security.Permissions.FileIOPermission> objekt reprezentující přístup pro zápis k C:\Test.txt. (Oprávnění k zápisu je potřebné k odstranění souboru). Kód poté vyvolá imperativní kontrola zabezpečení voláním **FileIOPermission** objektu **vyžádání** metody. Pokud jeden z volající v zásobníku volání nemá žádné toto oprávnění, <xref:System.Security.SecurityException> je vyvolána výjimka. Pokud není vyvolána žádná výjimka, víte, že všichni volající nemá oprávnění k přístupu k C:\Test.txt. Protože si myslíte, že většina vašich volající nemá oprávnění pro přístup k nespravovaným kódem, váš kód poté vytvoří <xref:System.Security.Permissions.SecurityPermission> objekt, který představuje oprávnění pro volání nespravovaného kódu a volá objektu **Assert** metody. Nakonec se volá nespravovanou funkci Win32 odstranit C:\Text.txt a vrátí řízení volajícímu.  
  
> [!CAUTION]
>  Je nutné zajistit, že váš kód v situacích, kdy může být použít jiný kód pro přístup k prostředku, který je chráněn oprávnění, které uplatňujete nepoužívá kontrolní výrazy. Například v kódu, která zapisuje do souboru, jejíž název je zadán jako parametr volající by uplatnit **FileIOPermission** pro zápis do souborů, protože váš kód by být otevřený, aby zneužití třetí stranou.  
  
 Při použití imperativní syntaxe zabezpečení volání **Assert** metoda na více oprávnění ve stejné metody způsobí, že výjimka zabezpečení, která je vyvolána. Místo toho byste měli vytvořit **PermissionSet** objektu, předejte ji jednotlivá oprávnění chcete vyvolat a následně zavolat **Assert** metodu **PermissionSet** objekt. Můžete volat **Assert** metodu více než jednou při použití syntaxe deklarativní zabezpečení.  
  
 Následující příklad ukazuje deklarativní syntaxe pro přepsání zabezpečení ověří pomocí **Assert** metody. Všimněte si, že **FileIOPermissionAttribute** syntaxe má dvě hodnoty: <xref:System.Security.Permissions.SecurityAction> výčet a umístění souboru nebo adresáři, do kterého má být udělena oprávnění. Volání **Assert** způsobí, že požadavky pro přístup k `C:\Log.txt` proběhla úspěšně, i když volající nejsou kontroluje oprávnění pro přístup k souboru.  
  
```vb  
Option Explicit  
Option Strict  
  
Imports System  
Imports System.IO  
Imports System.Security.Permissions  
  
Namespace LogUtil  
   Public Class Log  
      Public Sub New()  
  
      End Sub  
  
     <FileIOPermission(SecurityAction.Assert, All := "C:\Log.txt")> Public Sub   
      MakeLog()  
         Dim TextStream As New StreamWriter("C:\Log.txt")  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now) '  
         TextStream.Close()  
      End Sub  
   End Class  
End Namespace  
```  
  
```csharp  
namespace LogUtil  
{  
   using System;  
   using System.IO;  
   using System.Security.Permissions;  
  
   public class Log  
   {  
      public Log()  
      {      
      }     
      [FileIOPermission(SecurityAction.Assert, All = @"C:\Log.txt")]  
      public void MakeLog()  
      {     
         StreamWriter TextStream = new StreamWriter(@"C:\Log.txt");  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now);  
         TextStream.Close();  
      }  
   }  
}   
```  
  
 Následující fragmenty kódu ukazují imperativní syntaxe pro přepsání zabezpečení ověří pomocí **Assert** metody. V tomto příkladu instance **FileIOPermission** deklaraci objektu. Je předán konstruktoru **FileIOPermissionAccess.AllAccess** definovat typ přístupu povolený, za nímž následuje řetězec, který popisuje umístění souboru. Jednou **FileIOPermission** objekt je definovaný, je třeba volat jeho **Assert** metodu pro přepsání kontroly zabezpečení.  
  
```vb  
Option Explicit  
Option Strict  
Imports System  
Imports System.IO  
Imports System.Security.Permissions  
Namespace LogUtil  
   Public Class Log  
      Public Sub New()  
      End Sub 'New  
  
      Public Sub MakeLog()  
         Dim FilePermission As New FileIOPermission(FileIOPermissionAccess.AllAccess, "C:\Log.txt")  
         FilePermission.Assert()  
         Dim TextStream As New StreamWriter("C:\Log.txt")  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now)  
         TextStream.Close()  
      End Sub  
   End Class  
End Namespace  
```  
  
```csharp  
namespace LogUtil  
{  
   using System;  
   using System.IO;  
   using System.Security.Permissions;  
  
   public class Log  
   {  
      public Log()  
      {      
      }     
      public void MakeLog()  
      {  
         FileIOPermission FilePermission = new FileIOPermission(FileIOPermissionAccess.AllAccess,@"C:\Log.txt");   
         FilePermission.Assert();  
         StreamWriter TextStream = new StreamWriter(@"C:\Log.txt");  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now);  
         TextStream.Close();  
      }  
   }  
}  
```  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Security.PermissionSet>
- <xref:System.Security.Permissions.SecurityPermission>
- <xref:System.Security.Permissions.FileIOPermission>
- <xref:System.Security.Permissions.SecurityAction>
- [Atributy](../../../docs/standard/attributes/index.md)
- [Zabezpečení přístupu kódu](../../../docs/framework/misc/code-access-security.md)
