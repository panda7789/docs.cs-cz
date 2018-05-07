---
title: Mgmtclassgen.exe (spravovaný generátor tříd se silnými typy)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CIM types
- Management Strongly Typed Class Generator
- WMI class
- Mgmtclassgen.exe
- early-bound managed classes
ms.assetid: 02ce6699-49b5-4a0b-b0d5-1003c491232e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 282d6376b434121ed6d59297be2ce36ce361c589
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="mgmtclassgenexe-management-strongly-typed-class-generator"></a>Mgmtclassgen.exe (spravovaný generátor tříd se silnými typy)
Nástroj Management Strongly Typed Class Generator umožňuje rychle generovat spravovanou třídu s časnou vazbou pro zadanou třídu Windows Management Instrumentation (WMI). Vygenerovaná třída usnadňuje psaní kódu pro přístup k instanci třídy WMI.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
mgmtclassgen   
WMIClass [options]   
```  
  
|Argument|Popis|  
|--------------|-----------------|  
|*WMIClass*|Třída WMI, pro kterou chcete generovat spravovanou třídu s časnou vazbou.|  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/l***jazyk* |Určuje jazyk, ve kterém chcete vygenerovat spravovanou třídu s časnou vazbou. Můžete zadat **CS** (C#, výchozí), **VB** (Visual Basic), **MC** (C++), nebo **JS** (JScript) jako argument jazyk.|  
|**/m***počítače* |Určuje počítač, na kterém je uložena třída WMI a ke kterému je třeba se připojit. Výchozí hodnotou je místní počítač.|  
|**/ n***cesta* |Určuje cestu k oboru názvů služby WMI, který obsahuje třídu WMI. Pokud nezadáte tuto možnost, nástroj vygeneruje kód pro *WMIClass* ve výchozí **Root\cimv2** oboru názvů.|  
|**/o***classnamespace* |Určuje obor názvů .NET, ve kterém chcete vygenerovat spravovanou třídu kódů. Pokud tuto možnost nezadáte, nástroj vygeneruje obor názvů pomocí oboru názvů WMI a předpony schématu. Předpona schématu je část názvu třídy před podtržítkem. Například **Win32_OperatingSystem** třídy v **Root\cimv2** obor názvů, nástroj vygeneruje třídy v **ROOT. CIMV2. Win32**.|  
|**/p***filepath* |Určuje cestu k souboru, do kterého chcete uložit vygenerovaný kód. Pokud tuto možnost nezadáte, nástroj vytvoří soubor v aktuálním adresáři. Ho názvů, třídy a soubor, ve kterém vygeneruje třídy pomocí *WMIClass* argument. Název třídy a soubor je stejný jako název *WMIClass.* Pokud *WMIClass* obsahuje znak podtržítka, nástroj používá část názvu třídy následující znak podtržítka. Například pokud *WMIClass* název je ve formátu **Win32_LogicalDisk**, vygenerované třídy a soubor je s názvem "logický disk". Pokud soubor již existuje, nástroj přepíše existující soubor.|  
|**/pW***heslo* |Určuje heslo pro použití při přihlašování k počítači určeném parametrem **/m** možnost.|  
|**/u***uživatelské jméno* |Určuje uživatelské jméno pro použití při přihlašování k počítači určeném parametrem **/m** možnost.|  
|**/?**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
  
## <a name="remarks"></a>Poznámky  
 MgmtClassGen.exe používá <xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=nameWithType> metoda. Proto můžete použít libovolného zprostředkovatele vlastního kódu k vygenerování kódu v jiných spravovaných jazycích než C#, Visual Basic a JScript.  
  
 Vygenerované třídy jsou svázány se schématem, pro které byly vygenerovány. Pokud se změní podkladové schéma, musíte znovu vygenerovat třídu, jestliže chcete, aby se změny projevily ve schématu.  
  
 Následující tabulka ukazuje, jak mapovat model WMI Common Information Model (CIM) na datové typy ve vygenerované třídě:  
  
|Typ CIM|Datový typ ve vygenerované třídě|  
|--------------|--------------------------------------|  
|CIM_SINT8|**SByte –**|  
|CIM_UINT8|**Bajtů**|  
|CIM_SINT16|**Int16**|  
|CIM_UINT16|**UInt16**|  
|CIM_SINT32|**Int32**|  
|SIM_UINT32|**UInt32**|  
|CIM_SINT64|**Int64**|  
|CIM_UINT64|**UInt64**|  
|CIM_REAL32|**Jeden**|  
|CIM_REAL64|**Double**|  
|CIM_BOOLEAN|**Logická hodnota**|  
|CIM_String|**Řetězec**|  
|CIM_DATETIME|**Data a času** nebo **časový interval**|  
|CIM_REFERENCE|**Cesta ManagementPath nadřízeného**|  
|CIM_CHAR16|**Char**|  
|CIM_OBJECT|**ManagementBaseObject**|  
|CIM_IUNKNOWN|**Objekt**|  
|CIM_ARRAY|Pole objektů uvedených výše|  
  
 Při generování třídy WMI si všimněte následujícího chování:  
  
-   Standardní veřejná vlastnost nebo metoda může mít stejný název jako existující vlastnost nebo metoda. V tomto případě nástroj změní název vlastnosti nebo metody ve vygenerované třídě, aby předešel konfliktům názvů.  
  
-   Název vlastnosti nebo metody ve vygenerované třídě může být klíčovým slovem v cílovém programovacím jazyku. V tomto případě nástroj změní název vlastnosti nebo metody ve vygenerované třídě, aby předešel konfliktům názvů.  
  
-   Kvalifikátory jsou ve službě WMI modifikátory obsahující informace popisující třídu, instanci, vlastnost nebo metodu. WMI používá standardní kvalifikátory například **čtení**, **zápisu**, a **klíč** k popisu na vlastnost ve vygenerované třídy. Například vlastnost, která je změnit, **čtení** kvalifikátor je definována pouze pomocí vlastnosti **získat** přistupujícího objektu v vygenerované třídy. Protože je vlastnost označena **čtení** kvalifikátor má být jen pro čtení, **nastavit** přistupujícího objektu není definován.  
  
-   Číselná vlastnost mohou být upravena **hodnoty** a **ValueMaps** kvalifikátory indikující, že vlastnost lze nastavit pouze na zadané přípustné hodnoty. Výčet je generována pomocí těchto **hodnoty** a **ValueMaps** a vlastnost je mapována na výčtu.  
  
-   Služba WMI používá k popisu třídy, která může mít pouze jednu instanci, pojem singleton. Výchozí konstruktor pro třídu singleton inicializuje tuto třídu pouze pro jedinou instanci třídy.  
  
-   Třída WMI může mít vlastnosti, které jsou objekty. Při generování třídy silného typu pro tento typ třídy WMI byste měli zvážit vygenerování třídy silného typu pro typy vlastností vloženého objektu. To vám umožní přístup k vloženým objektům silně typovaným způsobem. Vygenerovaný kód nemusí být schopen rozpoznat typ vloženého objektu. V tomto případě bude v generovaném kódu vytvořen komentář, který vás na tento problém upozorní. Pak můžete vygenerovaný kód upravit a zadat vlastnost pro další generovanou třídu.  
  
-   Ve službě WMI mohou datové hodnoty datového typu CIM_DATETIME představovat konkrétní datum a čas nebo časový interval. Pokud hodnota dat představuje datum a čas, je datového typu ve generovaná třída **data a času**. Pokud hodnota dat představuje časový interval, je datového typu ve generovaná třída **časový interval**.  
  
 Případně můžete vygenerovat třídu silného typu pomocí rozšíření Server Explorer Management Extension aplikace Visual Studio .NET.  
  
 Další informace o rozhraní WMI najdete v tématu **Windows Management Instrumentation** tématu v dokumentaci platformy sady SDK.  
  
## <a name="examples"></a>Příklady  
 Následující příkaz vytvoří spravovanou třídou v kódu jazyka C# pro **Win32_LogicalDisk** třídy WMI v **Root\cimv2** oboru názvů. Tento nástroj zapisuje spravované třídy ke zdrojovému souboru v c:\disk.cs v **ROOT. CIMV2. Win32** oboru názvů.  
  
```  
mgmtclassgen Win32_LogicalDisk /n root\cimv2 /l CS /p c:\disk.cs  
```  
  
 Následující příklad kódu ukazuje, jak používat vygenerovanou třídu při programování. Nejprve se vypočítá instance třídy a vytiskne se cesta. Poté se pomocí instance WMI vytvoří instance generované třídy, která má být inicializována. `Process` je třída vygenerované **Win32_Process** a `LogicalDisk` je třída vygenerované **Win32_LogicalDisk** v **Root\cimv2** oboru názvů.  
  
```vb  
Imports System  
Imports System.Management  
Imports ROOT.CIMV2.Win32  
  
Public Class App     
   Public Shared Sub Main()        
      ' Enumerate instances of the Win32_process.  
      ' Print the Name property of the instance.  
      Dim ps As Process     
      For Each ps In  Process.GetInstances()  
         Console.WriteLine(ps.Name)  
      Next ps  
  
      ' Initialize the instance of LogicalDisk with  
      ' the WMI instance pointing to logical drive d:.  
      Dim dskD As New LogicalDisk(New _  
         ManagementPath("win32_LogicalDisk.DeviceId=""d:"""))  
      Console.WriteLine(dskD.Caption)  
   End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.Management;  
using ROOT.CIMV2.Win32;  
  
public class App  
{  
   public static void Main()  
   {  
      // Enumerate instances of the Win32_process.  
      // Print the Name property of the instance.  
      foreach(Process ps in Process.GetInstances())  
      {  
         Console.WriteLine(ps.Name);  
      }  
  
      // Initialize the instance of LogicalDisk with  
      // the WMI instance pointing to logical drive d:.  
      LogicalDisk dskD = new LogicalDisk(new ManagementPath(  
        "win32_LogicalDisk.DeviceId=\"d:\""));  
      Console.WriteLine(dskD.Caption);  
   }  
}  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Management>  
 <xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=nameWithType>  
 <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>  
 [Nástroje](../../../docs/framework/tools/index.md)  
 [Příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
