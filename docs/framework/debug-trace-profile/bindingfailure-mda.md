---
title: "bindingFailure – pomocník spravovaného ladění (MDA)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- binding failure
- binding, failures
- MDAs (managed debugging assistants), binding failures
- assemblies [.NET Framework], binding failures
- managed debugging assistants (MDAs), binding failures
- BindingFailure MDA
ms.assetid: 26ada5af-175c-4576-931a-9f07fa1723e9
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fc87000e5b3f3a0f464929764eaeafaab4c3089a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="bindingfailure-mda"></a>bindingFailure – pomocník spravovaného ladění (MDA)
`bindingFailure` Pomocník spravovaného ladění (MDA) se aktivuje, když se nepodaří načíst sestavení.  
  
## <a name="symptoms"></a>Příznaky  
 Kód se pokusil o načtení sestavení pomocí statické odkaz nebo jednu z metod zavaděč, jako třeba <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> nebo <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>. Sestavení není načíst a <xref:System.IO.FileNotFoundException> nebo <xref:System.IO.FileLoadException> je vyvolána výjimka.  
  
## <a name="cause"></a>příčina  
 Selhání vazby nastane, když se nepodařilo načíst sestavení modulu runtime. Selhání vazby může být výsledkem jednoho z následujících situací:  
  
-   Modul CLR (CLR) nelze najít požadovaný sestavení. Existuje mnoho důvodů této situaci může dojít, jako je například sestavení, není nainstalována nebo není správně nakonfigurován k vyhledání sestavení aplikace.  
  
-   Běžný scénář problému dojde k předání typu do jiné domény aplikace, které vyžaduje CLR se načíst sestavení obsahující daný typ v jiné doméně aplikace. Nemusí být možné pro modul runtime k načtení sestavení, pokud jiné doméně aplikace je nakonfigurována jinak než původní domény aplikace. Například může mít dva aplikační domény různých <xref:System.AppDomain.BaseDirectory%2A> hodnot vlastností.  
  
-   Požadovaný sestavení je poškozený nebo není sestavení.  
  
-   Kód pokusu o načtení sestavení nemá správný kód přístupová oprávnění zabezpečení k načtení sestavení.  
  
-   Přihlašovací údaje uživatele nemají potřebná oprávnění pro čtení tohoto souboru.  
  
## <a name="resolution"></a>Rozlišení  
 Prvním krokem je určit, proč modulu CLR nelze vytvořit vazbu na požadovaný sestavení. Existuje mnoho důvodů, proč nemusí mít modulu runtime nalezeno nebo bylo možné zatížení požadovaný sestavení, např. scénáře uvedené v části Příčina. K vyloučení příčinou selhání vazby doporučujeme následující akce:  
  
-   Zjistit příčinu na základě dat poskytované `bindingFailure` (mda):  
  
    -   Spustit [Fuslogvw.exe (sestavení vazby Log Viewer)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) ke čtení v souborech protokolů chyb vyprodukované vazač sestavení.  
  
    -   Určí, zda je sestavení v umístění požadovaný. U <xref:System.Reflection.Assembly.LoadFrom%2A> a <xref:System.Reflection.Assembly.LoadFile%2A> metody, požadované umístění se dá snadno určit. U <xref:System.Reflection.Assembly.Load%2A> metodu, která sváže pomocí identity sestavení, které hledáte sestavení, které odpovídají této identity v doméně aplikace <xref:System.AppDomain.BaseDirectory%2A> cesta testu vlastnosti a globální mezipaměti sestavení.  
  
-   Vyřešte příčinu založena na předchozí určení. Možným řešením možnosti jsou následující:  
  
    -   Nainstalujte požadovaný sestavení v globální mezipaměti sestavení a volání. <xref:System.Reflection.Assembly.Load%2A>Metoda pro načtení sestavení identita.  
  
    -   Zkopírujte požadované sestavení do adresáře aplikace a volání <xref:System.Reflection.Assembly.Load%2A> metoda pro načtení sestavení identita.  
  
    -   Znovu nakonfigurujte doménu aplikace, v němž došlo k selhání vazby zahrnout cesta k sestavení můžete buď změnit <xref:System.AppDomain.BaseDirectory%2A> vlastnost nebo přidání privátní testování cesty.  
  
    -   Změna seznamu řízení přístupu pro soubor umožňující přihlášeného uživatele pro čtení tohoto souboru.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modulu Runtime  
 Tato MDA nemá žádný vliv na modulu CLR. Pouze sestavy data o selhání vazby.  
  
## <a name="output"></a>Výstup  
 MDA sestav sestavení, které se nepodařilo načíst, včetně požadovanou cestu nebo zobrazit název, kontext vazby, doménu aplikace, ve kterém byl požadován zatížení a příčinu selhání.  
  
 Zobrazovaný název nebo požadovaná cesta může být prázdná, pokud tato data nebyla k dispozici pro modulu CLR. Pokud bylo volání, který selhal <xref:System.Reflection.Assembly.Load%2A> metoda, je pravděpodobné, modul runtime nelze určit, zobrazovaný název sestavení.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <bindingFailure />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje situace, které můžou aktivovat tuto (mda):  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.Reflection;  
namespace ConsoleApplication1  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // This call attempts to load a nonexistent assembly.  
            // The call will throw a System.IO.FileNotFound exception  
            // and cause the activation of the bindingFailure MDA   
            // if it is registered.  
            Assembly.Load("NonExistentAssembly");  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
