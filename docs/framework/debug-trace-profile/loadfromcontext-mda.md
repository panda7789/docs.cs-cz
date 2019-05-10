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
ms.openlocfilehash: 632d9119cf32aab66c87e345ec98c6867ed51592
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64614373"
---
# <a name="loadfromcontext-mda"></a>loadFromContext – pomocník spravovaného ladění (MDA)
`loadFromContext` Pomocníka spravovaného ladění (MDA) se aktivuje, pokud je sestavení načteno do `LoadFrom` kontextu. Tato situace může nastat v důsledku volání <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> nebo další podobné metody.  
  
## <a name="symptoms"></a>Příznaky  
 Pomocí některé metody zavaděč může vést k načítání v sestavení `LoadFrom` kontextu. Použití tohoto kontextu může způsobit neočekávané chování pro serializaci, přetypování a řešení závislostí. Obecně je vhodné, že sestavení načtena do `Load` kontext k těmto problémům vyhnout. Je obtížné určit kontext sestavení bylo načteno do bez toto MDA.  
  
## <a name="cause"></a>Příčina  
 Obecně platí, bylo načteno do sestavení `LoadFrom` kontextu, pokud byl načten z cesty `Load` kontextu, jako je například globální mezipaměti sestavení nebo <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> vlastnost.  
  
## <a name="resolution"></a>Řešení  
 Konfigurace aplikací tak, aby <xref:System.Reflection.Assembly.LoadFrom%2A> volání už nejsou potřeba. Následující postupy můžete to udělat:  
  
- Nainstalujte sestavení v globální mezipaměti sestavení.  
  
- Sestavení v umístit <xref:System.AppDomainSetup.ApplicationBase%2A> adresář <xref:System.AppDomain>. V případě výchozí doménu <xref:System.AppDomainSetup.ApplicationBase%2A> adresář je ten, který obsahuje spustitelný soubor, který spustil proces. To může také vyžadovat vytvoření nového <xref:System.AppDomain> Pokud není vhodné přesunout sestavení.  
  
- Přidáte cesta zjišťování (.config) konfigurační soubor aplikace nebo sekundární aplikačních doménách, pokud jsou závislé sestavení v adresářích podřízené vzhledem ke spustitelnému souboru.  
  
 V obou případech lze změnit kód určený <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul Runtime  
 MDA nemá žádný vliv na CLR. Oznámí kontext, který se použil jako výsledek požadavku na zatížení.  
  
## <a name="output"></a>Výstup  
 MDA hlásí, že sestavení bylo načteno do `LoadFrom` kontextu. Určuje jednoduchý název sestavení a cestu. Rovněž navrhuje způsoby zmírnění rizik, abyste se vyhnuli použití `LoadFrom` kontextu.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <loadFromContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje situaci, která může aktivovat toto MDA:  
  
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
  
## <a name="see-also"></a>Viz také:

- [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
