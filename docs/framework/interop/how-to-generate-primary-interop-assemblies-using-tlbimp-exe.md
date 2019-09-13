---
title: 'Postupy: Generování primárních sestavení vzájemné spolupráce pomocí Tlbimp.exe'
ms.date: 03/30/2017
helpviewer_keywords:
- primary interop assemblies, generating
- Tlbimp.exe
- Type Library Importer
ms.assetid: 5419011c-6e57-40f6-8c65-386db8f7a651
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5d88da9a043aa2ed75b25f1c59fa991b97576d52
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894212"
---
# <a name="how-to-generate-primary-interop-assemblies-using-tlbimpexe"></a>Postupy: Generování primárních sestavení vzájemné spolupráce pomocí Tlbimp.exe

Existují dva způsoby, jak vytvořit primární definiční sestavení:

- Použití nástroje pro [Import knihovny typů (Tlbimp. exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) , který poskytuje Windows SDK.

  Nejjednodušším způsobem, jak vydávat primární spolupracující sestavení, je použití nástroje [Tlbimp. exe (importér knihovny typů)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md). Nástroj Tlbimp. exe poskytuje následující záruky:

  - Kontroluje další registrovaná sestavení primární spolupráce před vytvořením nových definičních sestavení pro všechny vnořené odkazy knihovny typů.

  - Nepovedlo se vygenerovat primární definiční sestavení, pokud nezadáte buď kontejner, nebo název souboru, aby bylo primární sestavení vzájemné spolupráce silného názvu.

  - Při vynechání odkazů na závislá sestavení se nepovedlo vygenerovat primární definiční sestavení.

  - Pokud přidáte odkazy na závislá sestavení, která nejsou sestaveními primární spolupráce, nemusíte vygenerovat primární definiční sestavení.

- Ruční vytváření sestavení primární spolupráce ve zdrojovém kódu pomocí jazyka, který je kompatibilní se specifikací CLS (Common Language Specification), jako je C#například. Tento přístup je užitečný v případě, že knihovna typů není k dispozici.

Pro podepsání sestavení silným názvem musíte mít pár kryptografických klíčů. Podrobnosti najdete v tématu [Vytvoření páru klíčů](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md).

### <a name="to-generate-a-primary-interop-assembly-using-tlbimpexe"></a>Generování primárního definičního sestavení pomocí nástroje Tlbimp. exe

1. V příkazovém řádku zadejte příkaz:

    **Tlbimp** *tlbfile* **/Primary/keyfile:** *název souboru* **/out:** *AssemblyName*

    V tomto příkazu je *tlbfile* soubor obsahující knihovnu typů modelu COM, název *souboru* je název kontejneru nebo souboru, který obsahuje dvojici klíčů, a *AssemblyName* je název sestavení pro podepsání silným názvem.

Primární spolupracující sestavení můžou odkazovat jenom na jiná primární spolupracující sestavení. Pokud vaše sestavení odkazuje na typy z knihovny typů modelu COM třetí strany, je nutné získat primární definiční sestavení od vydavatele před tím, než bude možné vygenerovat vaše primární definiční sestavení. Pokud jste Vydavatel, je nutné před generováním odkazujícího primárního sestavení vzájemné spolupráce vygenerovat primární definiční sestavení pro závislou knihovnu typů.

Závislé primární sestavení vzájemné spolupráce s číslem verze, které se liší od původní knihovny typů, není zjistitelné, když je nainstalován v aktuálním adresáři. Je nutné buď zaregistrovat závislé primární definiční sestavení v registru systému Windows, nebo použít možnost **/reference** a ověřit, zda nástroj Tlbimp. exe najde závislou knihovnu DLL.

Můžete také zabalit více verzí knihovny typů. Pokyny najdete v tématu [postup: Zabalte více verzí knihoven](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/1565h6hc(v=vs.100))typů.

## <a name="example"></a>Příklad

Následující příklad importuje knihovnu `LibUtil.tlb` typů modelu COM a podepíše sestavení `LibUtil.dll` se silným názvem pomocí souboru `CompanyA.snk`klíče. Vynecháte-li konkrétní název oboru názvů, tento příklad vytvoří výchozí obor `LibUtil`názvů.

```console
tlbimp LibUtil.tlb /primary /keyfile:CompanyA.snk /out:LibUtil.dll
```

Pro výstižnější název (pomocí *dodavatele*. *Název knihovny* – zásady pojmenování: v následujícím příkladu je popsán výchozí název souboru sestavení a název oboru názvů.

```console
tlbimp LibUtil.tlb /primary /keyfile:CompanyA.snk /namespace:CompanyA.LibUtil /out:CompanyA.LibUtil.dll
```

Následující příklad importuje `MyLib.tlb`, který odkazuje `CompanyA.LibUtil.dll`a podepíše sestavení `CompanyB.MyLib.dll` silným názvem pomocí souboru `CompanyB.snk`klíče. Obor názvů `CompanyB.MyLib`přepíše výchozí název oboru názvů.

```console
tlbimp MyLib.tlb /primary /keyfile:CompanyB.snk /namespace:CompanyB.MyLib /reference:CompanyA.LibUtil.dll /out:CompanyB.MyLib.dll
```

## <a name="see-also"></a>Viz také:

- [Postupy: Registrovat primární spolupracující sestavení](../../../docs/framework/interop/how-to-register-primary-interop-assemblies.md)
