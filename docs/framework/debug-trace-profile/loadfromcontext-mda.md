---
title: loadFromContext – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), LoadFrom context
- managed debugging assistants (MDAs), LoadFrom context
- LoadFrom context
- LoadFromContext MDA
ms.assetid: a9b14db1-d3a9-4150-a767-dcf3aea0071a
ms.openlocfilehash: d0090a0272d1c3b6175b351175689df1e1e4fdbd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181799"
---
# <a name="loadfromcontext-mda"></a>loadFromContext – pomocník spravovaného ladění (MDA)
Spravovaný `loadFromContext` pomocník pro ladění (MDA) je aktivován, `LoadFrom` pokud je sestavení načteno do kontextu. Tato situace může nastat <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> v důsledku volání nebo jiné podobné metody.  
  
## <a name="symptoms"></a>Příznaky  
 Použití některých metod zavaděče může mít `LoadFrom` za následek sestavení načtenv kontextu. Použití tohoto kontextu může mít za následek neočekávané chování pro serializaci, přetypování a řešení závislostí. Obecně se doporučuje, aby sestavení být `Load` načteny do kontextu, aby se zabránilo těmto problémům. Je obtížné určit, do kterého kontextu bylo sestavení načteno bez tohoto MDA.  
  
## <a name="cause"></a>Příčina  
 Obecně platí, že sestavení `LoadFrom` bylo načteno do kontextu, `Load` pokud bylo načteno z <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> cesty mimo kontext, jako je například globální mezipaměť sestavení nebo vlastnost.  
  
## <a name="resolution"></a>Řešení  
 Nakonfigurujte aplikace tak, aby <xref:System.Reflection.Assembly.LoadFrom%2A> volání již není potřeba. K tomu můžete použít následující techniky:  
  
- Nainstalujte sestavení do globální mezipaměti sestavení.  
  
- Umístěte sestavení do <xref:System.AppDomainSetup.ApplicationBase%2A> adresáře <xref:System.AppDomain>pro rozhraní . V případě výchozí domény je <xref:System.AppDomainSetup.ApplicationBase%2A> adresář ten, který obsahuje spustitelný soubor, který proces spustil. To může také vyžadovat <xref:System.AppDomain> vytvoření nového, pokud není vhodné přesunout sestavení.  
  
- Přidejte cestu zjišťování do souboru konfigurace aplikace (.config) nebo do sekundárních aplikačních domén, pokud jsou závislá sestavení v podřízených adresářích vzhledem ke spustitelnému souboru.  
  
 V každém případě kód lze změnit <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> na použití metody.  
  
## <a name="effect-on-the-runtime"></a>Vliv na běhový čas  
 MDA nemá žádný vliv na CLR. Hlásí kontext, který byl použit v důsledku požadavku na zatížení.  
  
## <a name="output"></a>Výstup  
 MDA hlásí, že sestavení bylo `LoadFrom` načteno do kontextu. Určuje jednoduchý název sestavení a cesty. Navrhuje také skutečnosti snižující závažnost `LoadFrom` rizika, aby se zabránilo použití kontextu.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <loadFromContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje situaci, která může aktivovat tento MDA:  
  
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
