---
title: loadFromContext – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), LoadFrom context
- managed debugging assistants (MDAs), LoadFrom context
- LoadFrom context
- LoadFromContext MDA
ms.assetid: a9b14db1-d3a9-4150-a767-dcf3aea0071a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e1ba65194c49f76bb5c29ed28b1b038c02cf1a59
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33393078"
---
# <a name="loadfromcontext-mda"></a>loadFromContext – pomocník spravovaného ladění (MDA)
`loadFromContext` Pomocník spravovaného ladění (MDA) se aktivuje, pokud je načtena do sestavení `LoadFrom` kontextu. Tato situace může nastat v důsledku volání <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> nebo jiné podobné metody.  
  
## <a name="symptoms"></a>Příznaky  
 Použití některé metody zavaděč může mít za následek načítá v sestavení `LoadFrom` kontextu. Použití tohoto kontextu může způsobit neočekávané chování pro serializaci, přetypování a zjištění závislosti. Obecně se doporučuje, aby sestavení být načtena do `Load` kontext, který má se těmto problémům vyhnuli. Je obtížné určit, které kontext sestavení bylo načteno do bez této (mda).  
  
## <a name="cause"></a>příčina  
 Obecně platí, sestavení bylo načteno do `LoadFrom` kontextu, pokud byla načtena z cesty mimo `Load` kontextu, jako je například globální mezipaměti sestavení nebo <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> vlastnost.  
  
## <a name="resolution"></a>Rozlišení  
 Konfigurace aplikací tak, aby <xref:System.Reflection.Assembly.LoadFrom%2A> volání už nejsou potřeba. Jak to udělat, můžete použít následující postupy:  
  
-   Instalace sestavení v globální mezipaměti sestavení.  
  
-   Sestavení v umístit <xref:System.AppDomainSetup.ApplicationBase%2A> adresář pro <xref:System.AppDomain>. V případě výchozí doménu <xref:System.AppDomainSetup.ApplicationBase%2A> adresář je ta, která obsahuje spustitelný soubor, který spustil proces. To může také vyžadovat vytvoření nové <xref:System.AppDomain> Pokud není vhodné pro přesun sestavení.  
  
-   Přidejte cestu k testování konfiguračním (config) souboru aplikace nebo sekundární aplikační domény, pokud jsou závislé sestavení v podřízených adresářích relativně ke spustitelnému souboru.  
  
 V každém případě může změnit kód tak, aby použít <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metoda.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modulu Runtime  
 MDA nemá žádný vliv na modulu CLR. Oznámí kontext, který byl použit jako výsledek požadavku na zatížení.  
  
## <a name="output"></a>Výstup  
 MDA hlásí, že sestavení bylo načteno do `LoadFrom` kontextu. Určuje jednoduchý název sestavení a cestu. Rovněž nabízí jejich zmírnění pro nepoužívejte `LoadFrom` kontextu.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <loadFromContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje situace, které můžou aktivovat tuto (mda):  
  
```  
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
 [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
