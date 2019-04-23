---
title: bindingFailure – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- binding failure
- binding, failures
- MDAs (managed debugging assistants), binding failures
- assemblies [.NET Framework], binding failures
- managed debugging assistants (MDAs), binding failures
- BindingFailure MDA
ms.assetid: 26ada5af-175c-4576-931a-9f07fa1723e9
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1e904d452b9f4a1b172d35984b752c0d97228338
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59480947"
---
# <a name="bindingfailure-mda"></a>bindingFailure – pomocník spravovaného ladění (MDA)

`bindingFailure` Pomocníka spravovaného ladění (MDA) se aktivuje, když sestavení se nepodaří načíst.

## <a name="symptoms"></a>Příznaky

Kód se pokusil o načtení sestavení pomocí statický odkaz nebo jednu z metod zavaděč, jako například <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> nebo <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>. Sestavení není načteno a <xref:System.IO.FileNotFoundException> nebo <xref:System.IO.FileLoadException> je vyvolána výjimka.

## <a name="cause"></a>Příčina

Když nelze načíst sestavení modulu runtime dojde k selhání vazby. Selhání vazby může být výsledkem jednoho z následujících situací:

- Modul CLR (CLR) nejde najít požadované sestavení. Existuje mnoho důvodů, že tato situace může nastat, jako je například sestavení není nainstalován nebo není správně nakonfigurován k vyhledání sestavení aplikace.

- Běžný scénář, kdy problém předává typ k jiné doméně aplikace, která vyžaduje CLR pro načtení sestavení obsahující daný typ v jiné doméně aplikace. Nemusí být možné pro modul runtime k načtení sestavení, pokud jiné doméně aplikace je nakonfigurována jinak než původní domény aplikace. Například může mít dvě domény aplikace různé <xref:System.AppDomain.BaseDirectory%2A> hodnot vlastností.

- Požadované sestavení je poškozený nebo se nejedná o sestavení.

- Kód pokusu o načtení sestavení nemá oprávnění zabezpečení přístupu ke správný kód pro načtení sestavení.

- Přihlašovací údaje uživatele nemají potřebná oprávnění ke čtení souboru.

## <a name="resolution"></a>Řešení

Prvním krokem je určit, proč nebylo možné vytvořit vazbu CLR na požadovaná sestavení. Existuje mnoho důvodů, proč nemusí mít modul runtime nalezen nebo je možné načíst požadovaná sestavení, jako je například scénáře uvedené v části Příčina. Tyto akce se doporučuje, aby eliminovat příčinou selhání vazby:

- Zjistit příčinu pomocí dat poskytované `bindingFailure` MDA:

  - Spustit [Fuslogvw.exe (Assembly Binding Log Viewer)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) číst protokoly chyb vytváří vázacím objektem sestavení.

  - Určení, zda je sestavení v požadované umístění. V případě třídy <xref:System.Reflection.Assembly.LoadFrom%2A> a <xref:System.Reflection.Assembly.LoadFile%2A> metody, požadované umístění se dá snadno určit. V případě třídy <xref:System.Reflection.Assembly.Load%2A> metodu, která vytvoří vazbu pomocí identity sestavení, musí vyhledat sestavení, která tuto identitu do domény aplikace odpovídají <xref:System.AppDomain.BaseDirectory%2A> cesta testu paměti pro vlastnost a globální mezipaměti sestavení.

- Vyřešte příčinu podle předchozího určení. Možným řešením možnosti jsou následující:

  - Nainstalujte požadované sestavení v globální mezipaměti sestavení a volání. <xref:System.Reflection.Assembly.Load%2A> Metoda pro načtení sestavení podle identity.

  - Zkopírujte požadované sestavení do adresáře aplikace a volání <xref:System.Reflection.Assembly.Load%2A> metodu pro načtení sestavení podle identity.

  - Změna konfigurace domény aplikace 00Z došlo k chybě vazby neobsahuje cestu k sestavení tak, že buď změníte <xref:System.AppDomain.BaseDirectory%2A> vlastnost nebo přidání privátní definovaných cest.

  - Změna seznamu řízení přístupu k souboru uživatel přihlášený ke čtení souboru.

## <a name="effect-on-the-runtime"></a>Vliv na modul Runtime

Toto MDA nemá žádný vliv na CLR. Sestavy pouze data o selhání vazby.

## <a name="output"></a>Výstup

MDA sestavy sestavení, které se nepodařilo načíst, včetně požadovanou cestu a/nebo zobrazované jméno, kontext vazby, domény aplikace, ve kterém byl vyžádán zatížení a důvod selhání.

Zobrazovaný název nebo požadovaná cesta může být prázdné, pokud tato data nebyla k dispozici pro modul CLR. Pokud bylo volání, které se nepovedlo <xref:System.Reflection.Assembly.Load%2A> metoda, je pravděpodobné, modul runtime nelze určit, zobrazovaný název sestavení.

## <a name="configuration"></a>Konfigurace

```xml
<mdaConfig>
  <assistants>
    <bindingFailure />
  </assistants>
</mdaConfig>
```

## <a name="example"></a>Příklad

Následující příklad kódu ukazuje situaci, která může aktivovat toto MDA:

```csharp
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

## <a name="see-also"></a>Viz také:

- [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
