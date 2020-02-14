---
title: loadFromContext – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), LoadFrom context
- managed debugging assistants (MDAs), LoadFrom context
- LoadFrom context
- LoadFromContext MDA
ms.assetid: a9b14db1-d3a9-4150-a767-dcf3aea0071a
ms.openlocfilehash: 28ef6e12c82cf5ca56962756b9ea964d0ae9baaa
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216163"
---
# <a name="loadfromcontext-mda"></a>loadFromContext – pomocník spravovaného ladění (MDA)
Pokud je sestavení načteno do kontextu `LoadFrom`, je aktivována aplikace `loadFromContext` Managed Debugging Assistant (MDA). Tato situace může nastat v důsledku volání <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> nebo jiných podobných metod.  
  
## <a name="symptoms"></a>Příznaky  
 Použití některých metod zavaděče může mít za následek načítání sestavení v kontextu `LoadFrom`. Použití tohoto kontextu může vést k neočekávanému chování při serializaci, přetypování a rozlišení závislostí. Obecně se doporučuje, aby byla sestavení načtena do `Load`ho kontextu, aby se předešlo těmto problémům. Je obtížné určit, který kontext bylo sestavení načteno bez tohoto MDA.  
  
## <a name="cause"></a>Příčina  
 Obecně platí, že sestavení bylo načteno do kontextu `LoadFrom`, pokud bylo načteno z cesty mimo `Load` kontext, jako je například globální mezipaměť sestavení (GAC) nebo vlastnost <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType>.  
  
## <a name="resolution"></a>Řešení  
 Konfigurace aplikací, například <xref:System.Reflection.Assembly.LoadFrom%2A> volání již nejsou potřeba. K tomu můžete použít následující postupy:  
  
- Nainstalujte sestavení do globální mezipaměti sestavení (GAC).  
  
- Pro <xref:System.AppDomain>umístěte sestavení do adresáře <xref:System.AppDomainSetup.ApplicationBase%2A>. V případě výchozí domény je <xref:System.AppDomainSetup.ApplicationBase%2A> adresářem, který obsahuje spustitelný soubor, který proces zahájil. To může také vyžadovat vytvoření nového <xref:System.AppDomain>, pokud není vhodné přesunout sestavení.  
  
- Přidejte cestu pro zjišťování do konfiguračního souboru aplikace (. config) nebo do domén sekundární aplikace, pokud jsou závislá sestavení v podřízených adresářích vzhledem ke spustitelnému souboru.  
  
 V každém případě může být kód změněn tak, aby používal metodu <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Modul MDA nemá žádný vliv na CLR. Oznamuje kontext, který byl použit jako výsledek žádosti o načtení.  
  
## <a name="output"></a>Výstup  
 MDA hlásí, že bylo sestavení načteno do kontextu `LoadFrom`. Určuje jednoduchý název sestavení a cesty. Navrhuje také zmírnění rizik, aby se předešlo použití `LoadFrom`ho kontextu.  
  
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
