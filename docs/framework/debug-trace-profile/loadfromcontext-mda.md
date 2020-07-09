---
title: loadFromContext – pomocník spravovaného ladění (MDA)
description: Pochopení pomocníka spravovaného ladění Loadfromcontext – (MDA) v rozhraní .NET, který se aktivuje, pokud je sestavení načteno do kontextu LoadFrom.
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), LoadFrom context
- managed debugging assistants (MDAs), LoadFrom context
- LoadFrom context
- LoadFromContext MDA
ms.assetid: a9b14db1-d3a9-4150-a767-dcf3aea0071a
ms.openlocfilehash: 8d55268f2b2106dde4e488a6f0271fd3b17349da
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051646"
---
# <a name="loadfromcontext-mda"></a>loadFromContext – pomocník spravovaného ladění (MDA)
`loadFromContext`Pokud je sestavení načteno do kontextu, je aktivován pomocník spravovaného ladění (MDA) `LoadFrom` . Tato situace může nastat v důsledku volání <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> nebo podobných metod.  
  
## <a name="symptoms"></a>Příznaky  
 Použití některých metod zavaděče může vést k tomu, že sestavení jsou načtena v `LoadFrom` kontextu. Použití tohoto kontextu může vést k neočekávanému chování při serializaci, přetypování a rozlišení závislostí. Obecně se doporučuje, aby byla sestavení načtena do kontextu, `Load` aby se tyto problémy předešly. Je obtížné určit, který kontext bylo sestavení načteno bez tohoto MDA.  
  
## <a name="cause"></a>Příčina  
 Obecně platí, že sestavení bylo načteno do `LoadFrom` kontextu, pokud bylo načteno z cesty mimo `Load` kontext, jako je například globální mezipaměť sestavení (GAC) nebo <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> vlastnost.  
  
## <a name="resolution"></a>Řešení  
 Nakonfigurujte aplikace tak, aby <xref:System.Reflection.Assembly.LoadFrom%2A> již nevyžadovaly volání. K tomu můžete použít následující postupy:  
  
- Nainstalujte sestavení do globální mezipaměti sestavení (GAC).  
  
- Umístěte sestavení do <xref:System.AppDomainSetup.ApplicationBase%2A> adresáře pro <xref:System.AppDomain> . V případě výchozí domény <xref:System.AppDomainSetup.ApplicationBase%2A> je adresář souborem, který obsahuje spustitelný soubor, který proces zahájil. To může také vyžadovat vytvoření nového, <xref:System.AppDomain> Pokud není vhodné přesunout sestavení.  
  
- Přidejte cestu pro zjišťování do konfiguračního souboru aplikace (. config) nebo do domén sekundární aplikace, pokud jsou závislá sestavení v podřízených adresářích vzhledem ke spustitelnému souboru.  
  
 V každém případě může být kód změněn tak, aby používal <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metodu.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Modul MDA nemá žádný vliv na CLR. Oznamuje kontext, který byl použit jako výsledek žádosti o načtení.  
  
## <a name="output"></a>Výstup  
 MDA hlásí, že sestavení bylo načteno do `LoadFrom` kontextu. Určuje jednoduchý název sestavení a cesty. Navrhuje také zmírnění rizik, aby nedocházelo k používání `LoadFrom` kontextu.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <loadFromContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje situaci, která může aktivovat Tento MDA:  
  
```csharp
using System.Reflection;  
namespace ConsoleApplication1  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // The following call caused the LoadFrom context to be used  
            // because the assembly is loaded using LoadFrom and the path is
            // located outside of the Load context probing path.
            Assembly.LoadFrom(@"C:\Text\Test.dll");  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Viz také

- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
