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
ms.openlocfilehash: ce281398fe7ea3a280355a7b79cc7144aba256be
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894644"
---
# <a name="mgmtclassgenexe-management-strongly-typed-class-generator"></a>Mgmtclassgen.exe (spravovaný generátor tříd se silnými typy)
Nástroj Management Strongly Typed Class Generator umožňuje rychle generovat spravovanou třídu s časnou vazbou pro zadanou třídu Windows Management Instrumentation (WMI). Vygenerovaná třída usnadňuje psaní kódu pro přístup k instanci třídy WMI.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
mgmtclassgen   
WMIClass [options]   
```  
  
|Argument|Popis|  
|--------------|-----------------|  
|*WMIClass*|Třída WMI, pro kterou chcete generovat spravovanou třídu s časnou vazbou.|  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/l** *jazyka*|Určuje jazyk, ve kterém chcete vygenerovat spravovanou třídu s časnou vazbou. Jako argument jazyka můžete zadatC#cs (; default), **VB** (Visual Basic),C++ **MC** () nebo **js** (JScript).|  
|**/m** *počítač*|Určuje počítač, na kterém je uložena třída WMI a ke kterému je třeba se připojit. Výchozí hodnotou je místní počítač.|  
|**/n** *cesta*|Určuje cestu k oboru názvů služby WMI, který obsahuje třídu WMI. Pokud tuto možnost nezadáte, nástroj vygeneruje kód pro *WMIClass* ve výchozím oboru názvů **root\cimv2** .|  
|**/o** *classnamespace*|Určuje obor názvů .NET, ve kterém chcete vygenerovat spravovanou třídu kódů. Pokud tuto možnost nezadáte, nástroj vygeneruje obor názvů pomocí oboru názvů WMI a předpony schématu. Předpona schématu je část názvu třídy před podtržítkem. Například pro třídu **Win32_OperatingSystem** v oboru názvů **root\cimv2** nástroj vygeneruje třídu v **kořenovém adresáři. Cimv2. Win32**.|  
|**/p** *filepath*|Určuje cestu k souboru, do kterého chcete uložit vygenerovaný kód. Pokud tuto možnost nezadáte, nástroj vytvoří soubor v aktuálním adresáři. Pojmenovává třídu a soubor, ve kterém třídu generuje, pomocí argumentu *WMIClass* . Název třídy a souboru jsou stejné jako název *WMIClass.* Pokud *WMIClass* obsahuje znak podtržítka, nástroj použije část názvu třídy za znakem podtržítka. Například pokud je název *WMIClass* ve formátu **Win32_LogicalDisk**, vygenerovaná třída a soubor se jmenuje "logický disk". Pokud soubor již existuje, nástroj přepíše existující soubor.|  
|**/pW** *heslo*|Určuje heslo, které se má použít při přihlášení k počítači určenému možností **/m** .|  
|**/u** *uživatelské jméno*|Určuje uživatelské jméno, které se má použít při přihlášení k počítači určenému možností **/m** .|  
|**/?**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
  
## <a name="remarks"></a>Poznámky  
 Mgmtclassgen. exe používá <xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=nameWithType> metodu. Proto můžete použít libovolného zprostředkovatele vlastního kódu k vygenerování kódu v jiných spravovaných jazycích než C#, Visual Basic a JScript.  
  
 Vygenerované třídy jsou svázány se schématem, pro které byly vygenerovány. Pokud se změní podkladové schéma, musíte znovu vygenerovat třídu, jestliže chcete, aby se změny projevily ve schématu.  
  
 Následující tabulka ukazuje, jak mapovat model WMI Common Information Model (CIM) na datové typy ve vygenerované třídě:  
  
|Typ CIM|Datový typ ve vygenerované třídě|  
|--------------|--------------------------------------|  
|CIM_SINT8|**SByte**|  
|CIM_UINT8|**Bytové**|  
|CIM_SINT16|**Int16**|  
|CIM_UINT16|**UInt16**|  
|CIM_SINT32|**Int32**|  
|SIM_UINT32|**UInt32**|  
|CIM_SINT64|**Int64**|  
|CIM_UINT64|**UInt64**|  
|CIM_REAL32|**Konkrétní**|  
|CIM_REAL64|**Klepat**|  
|CIM_BOOLEAN|**Datový typ Boolean**|  
|CIM_String|**Řetězec**|  
|CIM_DATETIME|**Datum a čas** nebo **časový** rozsah|  
|CIM_REFERENCE|**ManagementPath**|  
|CIM_CHAR16|**Char**|  
|CIM_OBJECT|**ManagementBaseObject**|  
|CIM_IUNKNOWN|**objekt**|  
|CIM_ARRAY|Pole objektů uvedených výše|  
  
 Při generování třídy WMI si všimněte následujícího chování:  
  
- Standardní veřejná vlastnost nebo metoda může mít stejný název jako existující vlastnost nebo metoda. V tomto případě nástroj změní název vlastnosti nebo metody ve vygenerované třídě, aby předešel konfliktům názvů.  
  
- Název vlastnosti nebo metody ve vygenerované třídě může být klíčovým slovem v cílovém programovacím jazyku. V tomto případě nástroj změní název vlastnosti nebo metody ve vygenerované třídě, aby předešel konfliktům názvů.  
  
- Kvalifikátory jsou ve službě WMI modifikátory obsahující informace popisující třídu, instanci, vlastnost nebo metodu. Rozhraní WMI používá standardní kvalifikátory, jako je **čtení**, **zápis**a **klíč** , k popisu vlastnosti ve vygenerované třídě. Například vlastnost, která je upravena s kvalifikátorem **Read** , je definována pouze pomocí přístupového objektu **Get** ve vygenerované třídě. Vzhledem k tomu, že vlastnost označená kvalifikátorem **Read** je určena jen pro čtení, není definován přistupující objekt **set** .  
  
- Číselná vlastnost může být upravena **hodnotami** a kvalifikátory **ValueMaps** k označení toho, že vlastnost může být nastavena pouze na zadané přípustné hodnoty. Výčet se generuje s těmito **hodnotami** a **ValueMaps** a vlastnost je namapována na výčet.  
  
- Služba WMI používá k popisu třídy, která může mít pouze jednu instanci, pojem singleton. Proto konstruktor bez parametrů pro třídu singleton bude inicializovat třídu pouze do jediné instance třídy.  
  
- Třída WMI může mít vlastnosti, které jsou objekty. Při generování třídy silného typu pro tento typ třídy WMI byste měli zvážit vygenerování třídy silného typu pro typy vlastností vloženého objektu. To vám umožní přístup k vloženým objektům silně typovaným způsobem. Vygenerovaný kód nemusí být schopen rozpoznat typ vloženého objektu. V tomto případě bude v generovaném kódu vytvořen komentář, který vás na tento problém upozorní. Pak můžete vygenerovaný kód upravit a zadat vlastnost pro další generovanou třídu.  
  
- Ve službě WMI mohou datové hodnoty datového typu CIM_DATETIME představovat konkrétní datum a čas nebo časový interval. Pokud hodnota dat představuje datum a čas, datový typ ve vygenerované třídě je **DateTime**. Pokud hodnota dat představuje časový interval, datový typ ve vygenerované třídě je **TimeSpan**.  
  
 Případně můžete vygenerovat třídu silného typu pomocí rozšíření Server Explorer Management Extension aplikace Visual Studio .NET.  
  
 Další informace o rozhraní WMI naleznete v tématu **rozhraní WMI (Windows Management Instrumentation)** v dokumentaci k sadě SDK platformy.  
  
## <a name="examples"></a>Příklady  
 Následující příkaz vygeneruje spravovanou třídu v C# kódu pro třídu **Win32_LogicalDisk** WMI v oboru názvů **root\cimv2** . Nástroj zapíše spravovanou třídu do zdrojového souboru na c:\disk.cs v **kořenovém adresáři. Cimv2.** Obor názvů Win32.  
  
```console  
mgmtclassgen Win32_LogicalDisk /n root\cimv2 /l CS /p c:\disk.cs  
```  
  
 Následující příklad kódu ukazuje, jak používat vygenerovanou třídu při programování. Nejprve se vypočítá instance třídy a vytiskne se cesta. Poté se pomocí instance WMI vytvoří instance generované třídy, která má být inicializována. `Process`je třída vygenerovaná pro **Win32_Process** a `LogicalDisk` je třídou vytvořenou pro **Win32_LogicalDisk** v oboru názvů **root\cimv2** .  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Management>
- <xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=nameWithType>
- <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>
- [Nástroje](../../../docs/framework/tools/index.md)
- [Příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
