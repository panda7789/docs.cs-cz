---
title: bindingFailure – pomocník spravovaného ladění (MDA)
description: Přečtěte si o Pomocníkovi spravovaném ladění bindingFailure – (MDA), který se aktivuje, když se nepovede načíst sestavení v .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- binding failure
- binding, failures
- MDAs (managed debugging assistants), binding failures
- assemblies [.NET Framework], binding failures
- managed debugging assistants (MDAs), binding failures
- BindingFailure MDA
ms.assetid: 26ada5af-175c-4576-931a-9f07fa1723e9
ms.openlocfilehash: 98c7947c7e5d2a1f0af8c26744d3b292ed8cb4c4
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415625"
---
# <a name="bindingfailure-mda"></a>bindingFailure – pomocník spravovaného ladění (MDA)

`bindingFailure`Pokud se sestavení nepovede načíst, aktivuje se pomocník spravovaného ladění (MDA).

## <a name="symptoms"></a>Příznaky

Kód se pokusil načíst sestavení pomocí statického odkazu nebo jedné z metod zavaděče, například <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> nebo <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> . Sestavení není načteno a <xref:System.IO.FileNotFoundException> <xref:System.IO.FileLoadException> je vyvolána výjimka nebo.

## <a name="cause"></a>Příčina

K selhání vazby dojde v případě, že modul runtime nemůže načíst sestavení. Selhání vazby může být výsledkem jedné z následujících situací:

- Modul CLR (Common Language Runtime) nemůže najít požadované sestavení. K tomu může dojít z mnoha důvodů, jako je například sestavení, které není nainstalováno nebo aplikace není správně nakonfigurována pro vyhledání sestavení.

- Běžný scénář problému předává typ jiné doméně aplikace, která vyžaduje, aby CLR načetl sestavení obsahující tento typ do druhé domény aplikace. Může být možné, že modul runtime nebude moci načíst sestavení, pokud je jiná doména aplikace konfigurována odlišně od původní domény aplikace. Například dvě domény aplikace mohou mít různé <xref:System.AppDomain.BaseDirectory%2A> hodnoty vlastností.

- Požadované sestavení je poškozeno nebo se nejedná o sestavení.

- Kód, který se pokouší načíst sestavení, nemá správná oprávnění zabezpečení přístupu kódu k načtení sestavení.

- Přihlašovací údaje uživatele neposkytují požadovaná oprávnění ke čtení tohoto souboru.

## <a name="resolution"></a>Řešení

Prvním krokem je určit, proč se modul CLR nemůže přivážet k požadovanému sestavení. Existuje mnoho důvodů, proč modul runtime pravděpodobně nenajde nebo nedokázal načíst požadované sestavení, například scénáře uvedené v části Příčina. K odstranění příčiny selhání vazby doporučujeme následující akce:

- Určete příčinu pomocí dat poskytovaných v rámci aplikace `bindingFailure` MDA:

  - Spusťte [Fuslogvw.exe (Prohlížeč protokolů vazby sestavení)](../tools/fuslogvw-exe-assembly-binding-log-viewer.md) a přečtěte si protokoly chyb vytvořené pořadačem sestavení.

  - Určete, zda je sestavení v požadovaném umístění. V případě <xref:System.Reflection.Assembly.LoadFrom%2A> <xref:System.Reflection.Assembly.LoadFile%2A> metod a lze požadované umístění snadno určit. V případě <xref:System.Reflection.Assembly.Load%2A> metody, která se váže pomocí identity sestavení, je nutné vyhledat sestavení, která odpovídají této identitě v <xref:System.AppDomain.BaseDirectory%2A> cestě k vlastnostem vlastnosti domény aplikace a globální mezipaměti sestavení (GAC).

- Vyřešte příčinu na základě výše uvedeného rozhodnutí. Možné možnosti řešení jsou následující:

  - Nainstalujte požadované sestavení do globální mezipaměti sestavení (GAC) a zavolejte na. <xref:System.Reflection.Assembly.Load%2A>Metoda pro načtení sestavení podle identity

  - Zkopírujte požadované sestavení do adresáře aplikace a zavolejte <xref:System.Reflection.Assembly.Load%2A> metodu pro načtení sestavení podle identity.

  - Překonfigurujte doménu aplikace, ve které došlo k chybě vazby, aby zahrnovala cestu sestavení, a to buď změnou <xref:System.AppDomain.BaseDirectory%2A> vlastnosti, nebo přidáním privátních cest probingu.

  - Změňte seznam řízení přístupu pro soubor, aby mohl přihlášený uživatel číst soubor.

## <a name="effect-on-the-runtime"></a>Vliv na modul runtime

Tento MDA nemá žádný vliv na CLR. Oznamuje pouze data o chybách vazeb.

## <a name="output"></a>Výstup

MDA hlásí sestavení, které se nepodařilo načíst, včetně požadované cesty nebo zobrazovaného názvu, kontextu vazby, domény aplikace, v níž bylo zatížení vyžádáno, a důvodu chyby.

Pokud nejsou data pro CLR k dispozici, může být zobrazované jméno nebo požadovaná cesta prázdná. Pokud volání metody neproběhlo <xref:System.Reflection.Assembly.Load%2A> , je pravděpodobně modulem runtime určení zobrazovaného názvu pro sestavení.

## <a name="configuration"></a>Konfigurace

```xml
<mdaConfig>
  <assistants>
    <bindingFailure />
  </assistants>
</mdaConfig>
```

## <a name="example"></a>Příklad

Následující příklad kódu ukazuje situaci, která může aktivovat Tento MDA:

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

## <a name="see-also"></a>Viz také

- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
