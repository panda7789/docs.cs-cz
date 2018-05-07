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
ms.openlocfilehash: ea8be23eb6fd2500e59527890b874b8f19ec06d5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="using-the-assert-method"></a>Použití metody Assert
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <xref:System.Security.CodeAccessPermission.Assert%2A> představuje metodu, kterou lze volat na kód přístupové oprávnění třídy a na <xref:System.Security.PermissionSet> třídy. Můžete použít **Assert** aby váš kód (a podřízené volající) k provedení akce, které má oprávnění k provedení kódu, ale jeho volající nemusí mít oprávnění k provedení. Kontrolní výraz zabezpečení změní normální proces, který modul runtime provádí během kontroly zabezpečení. Pokud uplatňujete oprávnění, říká systému zabezpečení není ke kontrole volající kódu pro uplatňovaná oprávnění.  
  
> [!CAUTION]
>  Kontrolní výrazy používejte opatrně, protože mohou otevřít bezpečnostní díry a narušují modul runtime mechanismus pro vynucení omezení zabezpečení.  
  
 Kontrolní výrazy jsou užitečné v situacích, ve kterých knihovna volání nespravovaného kódu nebo provádí volání, které vyžaduje oprávnění, která nesouvisí se samozřejmě se zamýšlené použití této knihovny. Například všechny spravované kód, který musí mít volání nespravovaného kódu **SecurityPermission** s **UnmanagedCode** příznak. Kód, který nepochází z místního počítače, jako je například kód, který byl stažen z místního intranetu, nebudou ve výchozím nastavení udělit toto oprávnění. Proto aby kód, který byl stažen z místního intranetu, abyste mohli volání knihovny, která používá nespravovaného kódu, musí mít oprávnění prosazený knihovny. Kromě toho některé knihovny mohou provádět volání, která jsou viditelná pro volající a vyžadují zvláštní oprávnění.  
  
 Můžete také použít kontrolní výrazy v situacích, ve kterých kódu přistupuje k prostředku způsobem, který je úplně skrytá volajícím. Předpokládejme například, vaše knihovna získává informace z databáze, ale v procesu také čte informace z registru počítače. Protože vývojáře, kteří používají vaše knihovna nemají přístup ke zdroji, nemají žádný způsob, jejich kód vyžaduje **RegistryPermission** Chcete-li použít kód. Pokud se rozhodnete, že není přiměřené nebo nezbytné vyžadovat, aby volající kódu mají oprávnění pro přístup do registru, můžete v tomto případě uplatnit oprávnění pro čtení v registru. V takovém případě je vhodné pro knihovnu, která má uplatnit oprávnění tak, že volající bez **RegistryPermission** můžete použít knihovnu.  
  
 Kontrolní výraz ovlivňuje procházení zásobníku pouze v případě, že uplatňovaná oprávnění a oprávnění pro název podřízený volající jsou stejného typu a požadované oprávnění je podmnožinou uplatňovaná oprávnění. Například, pokud uplatňujete **FileIOPermission** pro čtení všech souborů na jednotce C a podřízený požadavek se provádí **FileIOPermission** ke čtení souborů v C:\Temp, mohou ovlivnit kontrolní výraz procházení zásobníku; ale pokud byl požadavek na **FileIOPermission** k zápisu na disk C, kontrolní výraz by mít žádný vliv.  
  
 Pokud chcete provést kontrolní výrazy, musí váš kód udělit oprávnění uplatňujete a <xref:System.Security.Permissions.SecurityPermission> představující práva ke kontrolní výrazy. I když může uplatňovat oprávnění, které nebylo uděleno kódu, kontrolní výraz by zbytečný, protože kontrola zabezpečení by selhat, než kontrolní výraz by mohl způsobit ho proběhla úspěšně.  
  
 Následující obrázek znázorňuje, co se stane, když používáte **Assert**. Předpokládejme, že se o sestavení A, B, C, E a F a dvě oprávnění P1 a P1A platí následující příkazy:  
  
-   P1A představuje práva ke čtení na jednotce C soubory s příponou .txt.  
  
-   P1 představuje práva ke čtení všech souborů na jednotce C.  
  
-   P1A a P1 jsou obě **FileIOPermission** typy a P1A je podmnožinou P1.  
  
-   Sestavení E a F bylo uděleno oprávnění P1A.  
  
-   Sestavení C bylo uděleno oprávnění P1.  
  
-   Sestavení A a B byla udělena oprávnění P1 ani P1A.  
  
-   Metoda A je obsažena v sestavení A, metoda B je obsažena v sestavení B a tak dále.  
  
 ![](../../../docs/framework/misc/media/assert.gif "Assert")  
Použití metody Assert  
  
 V tomto scénáři, volání metod A B, B volání jazyka C, C volání E a volání E F. Metoda C uplatňuje oprávnění ke čtení souborů na jednotce C (oprávnění P1) a metoda E požaduje oprávnění ke čtení soubory s příponou .txt na jednotce C (oprávnění P1A). Vyžádání v F vyskytne v době běhu, procházení zásobníku se provede na zkontrolujte oprávnění všech volajících F, počínaje E. E byla udělena oprávnění P1A tak procházení zásobníku pokračuje zkontrolujte oprávnění C, kde je zjištěno kontrolní výraz. Protože požadované oprávnění (P1A) je podmnožinou uplatňovaná oprávnění (P1), procházení zásobníku se zastaví a kontrola zabezpečení automaticky úspěšné. Že sestavením A a B nebylo uděleno oprávnění P1A nezáleží. Pomocí uplatňování P1, metoda C zajišťuje jeho volající přístup k prostředku chráněného P1, i v případě, že volající nebylo uděleno oprávnění pro přístup k prostředku.  
  
 Pokud návrh knihovny tříd a třída přistupuje k chráněnému prostředku, musí, ve většině případů provedete požadavek zabezpečení vyžaduje, aby volající třídy měli příslušné oprávnění. Pokud třída potom provádí operaci, pro které znáte většina volajících nebude mít oprávnění, a pokud jste ochotni převzít odpovědnost za to, že umožníte těmto volajícím volat váš kód, můžete uplatnit oprávnění voláním **Assert** metoda na objekt oprávnění, která představuje operaci provádí kód. Pomocí **Assert** tímto způsobem umožňuje volajícím za normálních okolností nemohli volat vašeho kódu. Proto pokud uplatňujete oprávnění, byste měli být nutné provést vhodné kontroly zabezpečení předem zabránit zneužitím příslušné součásti.  
  
 Předpokládejme například, že vysoce důvěryhodná knihovna tříd má metodu, která odstraní soubory. Voláním nespravované Win32 funkce přistupuje k souboru. Volající spustí váš kód **odstranit** metodu předáním názvu souboru, který má být odstraněna, C:\Test.txt. V rámci **odstranit** metoda, vytvoří kód <xref:System.Security.Permissions.FileIOPermission> objekt reprezentující přístup pro zápis do C:\Test.txt. (Přístup pro zápis je nutné pro odstranění souboru). Váš kód poté vyvolá imperativní kontrolu zabezpečení voláním **FileIOPermission** objektu **vyžádání** metoda. Pokud jeden z volajících v zásobníku volání nemá toto oprávnění, <xref:System.Security.SecurityException> je vyvolána výjimka. Pokud nedojde k výjimce, víte, že všechny volající mají oprávnění k přístupu k C:\Test.txt. Vzhledem k tomu, že budete mít dojem, že většina z vašich volajících nebude mít oprávnění pro přístup k nespravovanému kódu, váš kód poté vytvoří <xref:System.Security.Permissions.SecurityPermission> objekt, který reprezentuje právo pro volání nespravovaného kódu a zavolá metodu objektu **Assert** metoda. Nakonec volá funkci nespravované Win32 odstranit C:\Text.txt a vrátí prvek na volajícího.  
  
> [!CAUTION]
>  Je nutné zajistit, že váš kód nepoužívá kontrolní výrazy v situacích, kdy může být použít jiný kód pro přístup k prostředku, který je chráněný pomocí oprávnění, které uplatňujete. Například v kódu, který zapisuje do souboru, jehož název je zadán volající jako parametr, nebude uplatnit **FileIOPermission** pro zápis do souborů, protože váš kód by být otevřené pro zneužití třetí strany.  
  
 Při použití imperativní syntaxe zabezpečení volání **Assert** metoda na více oprávnění ve stejnou metodu způsobí vyvolání výjimky zabezpečení. Místo toho, měli byste vytvořit **Assert** objektu, předejte ji chcete vyvolat a pak zavolají jednotlivá oprávnění **Assert** metodu **Assert** objekt. Můžete volat **Assert** metoda více než jednou, když používáte deklarativní syntaxi zabezpečení.  
  
 Následující příklad ukazuje deklarativní syntaxe pro používání kontroly přepsání zabezpečení **Assert** metoda. Všimněte si, že **FileIOPermissionAttribute** syntaxe má dvě hodnoty: <xref:System.Security.Permissions.SecurityAction> výčet a umístění soubor nebo adresář, do kterého má být udělena oprávnění. Volání **Assert** způsobí, že požadavky pro přístup k `C:\Log.txt` úspěšné, i když nejsou kontrola volající oprávnění k přístupu k souboru.  
  
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
  
 Následující fragmenty kódu ukazují imperativní syntaxi pro přepsání zabezpečení zkontroluje pomocí **Assert** metoda. V tomto příkladu instanci **FileIOPermission** objekt deklarován. Jeho konstruktoru je předán **FileIOPermissionAccess.AllAccess** k definování typu přístupová oprávnění, následuje řetězec popisující umístění souboru. Jednou **FileIOPermission** objekt je definován, je třeba volat jeho **Assert** metodu pro přepsání kontroly zabezpečení.  
  
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
  
## <a name="see-also"></a>Viz také  
 <xref:System.Security.PermissionSet>  
 <xref:System.Security.Permissions.SecurityPermission>  
 <xref:System.Security.Permissions.FileIOPermission>  
 <xref:System.Security.Permissions.SecurityAction>  
 [Atributy](../../../docs/standard/attributes/index.md)  
 [Zabezpečení přístupu kódu](../../../docs/framework/misc/code-access-security.md)
