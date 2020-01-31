---
title: -bugreport
ms.date: 03/08/2018
helpviewer_keywords:
- -bugreport compiler option [Visual Basic]
- bugreport compiler option [Visual Basic]
- /bugreport compiler option [Visual Basic]
ms.assetid: e4325406-8dbd-4b48-b311-9ee0799e48bb
ms.openlocfilehash: 02d84bceb0242988c70889ddd5d3dc7530f6e808
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793551"
---
# <a name="-bugreport"></a>-bugreport

Vytvoří soubor, který můžete použít při zaznamenání zprávy o chybě.

## <a name="syntax"></a>Syntaxe

```console
-bugreport:file
```

## <a name="arguments"></a>Arguments

|Termín|Definice|
|---|---|
|`file`|Požadováno. Název souboru, který bude obsahovat zprávu o chybě. Uzavřete název souboru do uvozovek (""), pokud název obsahuje mezeru.|

## <a name="remarks"></a>Poznámky

Do `file`se přidají následující informace:

- Kopii všech souborů zdrojového kódu v kompilaci.

- Seznam možností kompilátoru použitých v kompilaci.

- Informace o verzi pro kompilátor, modul CLR (Common Language Runtime) a operační systém.

- Výstup kompilátoru, pokud existuje.

- Popis problému, pro který se zobrazí výzva.

- Popis toho, jak si myslíte problém, by měl být vyřešen, pro který se zobrazí výzva.

Vzhledem k tomu, že kopie všech souborů zdrojového kódu je součástí `file`, může být vhodné reprodukce (podezřelé) vady kódu v nejkratším možném programu.

> [!IMPORTANT]
> Možnost `-bugreport` vytvoří soubor, který obsahuje potenciálně citlivé informace. Patří sem aktuální čas, verze kompilátoru, verze .NET Framework, verze operačního systému, uživatelské jméno, argumenty příkazového řádku, s nimiž byl kompilátor spuštěn, veškerý zdrojový kód a binární forma libovolného odkazovaného sestavení. Tato možnost je k dispozici při zadání možností příkazového řádku v souboru Web. config pro kompilaci ASP.NET aplikace na straně serveru. Chcete-li tomu zabránit, upravte soubor Machine. config tak, aby nedocházelo k tomu, aby uživatelé mohli kompilovat na serveru.

Pokud je tato možnost použita s `-errorreport:prompt`, `-errorreport:queue`nebo `-errorreport:send`a vaše aplikace narazí na vnitřní chybu kompilátoru, informace v `file` se odešlou společnosti Microsoft Corporation. Tyto informace pomohou technikům Microsoftu identifikovat příčinu chyby a mohou pomoci zlepšit další vydání Visual Basic. Ve výchozím nastavení se Microsoftu neodesílají žádné informace. Pokud však zkompilujete aplikaci pomocí `-errorreport:queue`, která je ve výchozím nastavení povolena, aplikace shromáždí své zprávy o chybách. Až se správce počítače přihlásí, systém zasílání zpráv o chybách zobrazí automaticky otevírané okno, které správci umožní předávat společnosti Microsoft jakékoli zprávy o chybách, ke kterým došlo od přihlášení.

> [!NOTE]
> Možnost `-bugreport` není k dispozici ve vývojovém prostředí sady Visual Studio; je k dispozici pouze při kompilaci z příkazového řádku.

## <a name="example"></a>Příklad

Následující příklad zkompiluje *T2. vb* a vloží všechny informace o hlášení chyb do souboru *problém. txt*.

```console
vbc -bugreport:problem.txt t2.vb
```

## <a name="see-also"></a>Viz také:

- [Visual Basic Kompilátor příkazového řádku](index.md)
- [-Debug (Visual Basic)](debug.md)
- [-errorreport](errorreport.md)
- [Příkazové řádky ukázkové kompilace](sample-compilation-command-lines.md)
- [Element trustLevel pro securityPolicy (schéma nastavení ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/as399f0x(v=vs.100))
