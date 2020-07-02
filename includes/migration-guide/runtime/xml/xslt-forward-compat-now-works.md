---
ms.openlocfilehash: e3b9711ac66901d69838de4c9f309d086b06fd4d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620114"
---
### <a name="xslt-forward-compat-now-works"></a>Kompatibilita s přesměrováním XSLT teď funguje

#### <a name="details"></a>Podrobnosti

V .NET Framework 4 došlo k následujícím problémům s dopřednou kompatibilitou XSLT 1,0:<ul><li>Načítání šablony stylů se nezdařilo, pokud byla její verze nastavena jako 2.0 a analyzátor zjistil nerozpoznanou konstrukci XSLT 1.0.</li><li><code>xsl:sort</code>Konstrukce nedokázala seřadit data, pokud byla verze předlohy stylů nastavena na 1,1.</li></ul>V .NET Framework 4,5 byly tyto problémy vyřešeny a režim dopředné kompatibility XSLT 1,0 funguje správně.

#### <a name="suggestion"></a>Návrh

Většina aplikací by měla být neovlivněná, ale data se v některých případech řadí jinak v případě, že jsou dodržovány šablony stylů XSL: Sort. Pokud <code>xsl:sort</code> se používá v šablonách stylů 1,1, zkontrolujte, že aplikace nezávisí na neseřazeném pořadí dat. Pokud aplikace spoléhají na chování řazení 4,0, odeberte <code>xsl:sort</code> je ze seznamu stylů.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Edge|
|Verze|4.5|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Xml.Xsl.XslCompiledTransform?displayProperty=nameWithType></li></ul>|
