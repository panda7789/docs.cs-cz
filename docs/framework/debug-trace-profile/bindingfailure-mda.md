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
ms.openlocfilehash: e3a9a915d25cbe5f052f039055167cf3ae4bf424
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216915"
---
# <a name="bindingfailure-mda"></a>bindingFailure – pomocník spravovaného ladění (MDA)

Pokud se sestavení nepovede načíst, aktivuje se Pomocník pro spravované ladění v `bindingFailure` (MDA).

## <a name="symptoms"></a>Příznaky

Kód se pokusil načíst sestavení pomocí statického odkazu nebo jedné z metod zavaděče, například <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> nebo <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>. Sestavení není načteno a je vyvolána výjimka <xref:System.IO.FileNotFoundException> nebo <xref:System.IO.FileLoadException>.

## <a name="cause"></a>Příčina

K selhání vazby dojde v případě, že modul runtime nemůže načíst sestavení. Selhání vazby může být výsledkem jedné z následujících situací:

- Modul CLR (Common Language Runtime) nemůže najít požadované sestavení. K tomu může dojít z mnoha důvodů, jako je například sestavení, které není nainstalováno nebo aplikace není správně nakonfigurována pro vyhledání sestavení.

- Běžný scénář problému předává typ jiné doméně aplikace, která vyžaduje, aby CLR načetl sestavení obsahující tento typ do druhé domény aplikace. Může být možné, že modul runtime nebude moci načíst sestavení, pokud je jiná doména aplikace konfigurována odlišně od původní domény aplikace. Například dvě domény aplikace mohou mít různé <xref:System.AppDomain.BaseDirectory%2A> hodnoty vlastností.

- Požadované sestavení je poškozeno nebo se nejedná o sestavení.

- Kód, který se pokouší načíst sestavení, nemá správná oprávnění zabezpečení přístupu kódu k načtení sestavení.

- Přihlašovací údaje uživatele neposkytují požadovaná oprávnění ke čtení tohoto souboru.

## <a name="resolution"></a>Řešení

Prvním krokem je určit, proč se modul CLR nemůže přivážet k požadovanému sestavení. Existuje mnoho důvodů, proč modul runtime pravděpodobně nenajde nebo nedokázal načíst požadované sestavení, například scénáře uvedené v části Příčina. K odstranění příčiny selhání vazby doporučujeme následující akce:

- Určete příčinu pomocí dat poskytovaných `bindingFailure` MDA:

  - Spusťte [Fuslogvw. exe (Prohlížeč protokolu vazby sestavení)](../tools/fuslogvw-exe-assembly-binding-log-viewer.md) a přečtěte si protokoly chyb vytvořené pořadačem sestavení.

  - Určete, zda je sestavení v požadovaném umístění. V případě metod <xref:System.Reflection.Assembly.LoadFrom%2A> a <xref:System.Reflection.Assembly.LoadFile%2A> lze požadované umístění snadno určit. V případě metody <xref:System.Reflection.Assembly.Load%2A>, která vytváří vazby pomocí identity sestavení, je nutné vyhledat sestavení, která odpovídají této identitě v cestě k vlastnosti <xref:System.AppDomain.BaseDirectory%2A> a globální mezipaměti sestavení (GAC) domény aplikace.

- Vyřešte příčinu na základě výše uvedeného rozhodnutí. Možné možnosti řešení jsou následující:

  - Nainstalujte požadované sestavení do globální mezipaměti sestavení (GAC) a zavolejte na. Metoda <xref:System.Reflection.Assembly.Load%2A> pro načtení sestavení podle identity.

  - Zkopírujte požadované sestavení do adresáře aplikace a zavolejte metodu <xref:System.Reflection.Assembly.Load%2A> pro načtení sestavení podle identity.

  - Překonfigurujte doménu aplikace, ve které došlo k chybě vazby, aby zahrnovala cestu sestavení, buď změnou vlastnosti <xref:System.AppDomain.BaseDirectory%2A>, nebo přidáním privátních cest pro zjišťování.

  - Změňte seznam řízení přístupu pro soubor, aby mohl přihlášený uživatel číst soubor.

## <a name="effect-on-the-runtime"></a>Vliv na modul runtime

Tento MDA nemá žádný vliv na CLR. Oznamuje pouze data o chybách vazeb.

## <a name="output"></a>Výstup

MDA hlásí sestavení, které se nepodařilo načíst, včetně požadované cesty nebo zobrazovaného názvu, kontextu vazby, domény aplikace, v níž bylo zatížení vyžádáno, a důvodu chyby.

Pokud nejsou data pro CLR k dispozici, může být zobrazované jméno nebo požadovaná cesta prázdná. Pokud volání metody <xref:System.Reflection.Assembly.Load%2A> neúspěšné, je pravděpodobně modulem runtime určení zobrazovaného názvu pro sestavení.

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
