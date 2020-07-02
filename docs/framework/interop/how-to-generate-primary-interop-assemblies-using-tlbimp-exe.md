---
title: 'Postupy: Generování primárních sestavení vzájemné spolupráce pomocí Tlbimp.exe'
description: Naučte se generovat primární spolupracující sestavení pomocí nástroje pro import knihovny typů (Tlbimp.exe), který je k dispozici v Windows SDK.
ms.date: 03/30/2017
helpviewer_keywords:
- primary interop assemblies, generating
- Tlbimp.exe
- Type Library Importer
ms.assetid: 5419011c-6e57-40f6-8c65-386db8f7a651
ms.openlocfilehash: 779b4863b6f1513f3566d4ab31660d88cda1039b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619127"
---
# <a name="how-to-generate-primary-interop-assemblies-using-tlbimpexe"></a>Postupy: Generování primárních sestavení vzájemné spolupráce pomocí Tlbimp.exe

Existují dva způsoby, jak vytvořit primární definiční sestavení:

- Použití nástroje pro [Import knihovny typů (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md) poskytované Windows SDK.

  Nejjednodušší způsob, jak vypracovávat primární spolupracující sestavení, je použití [Tlbimp.exe (importér knihovny typů)](../tools/tlbimp-exe-type-library-importer.md). Tlbimp.exe poskytuje následující záruky:

  - Kontroluje další registrovaná sestavení primární spolupráce před vytvořením nových definičních sestavení pro všechny vnořené odkazy knihovny typů.

  - Nepovedlo se vygenerovat primární definiční sestavení, pokud nezadáte buď kontejner, nebo název souboru, aby bylo primární sestavení vzájemné spolupráce silného názvu.

  - Při vynechání odkazů na závislá sestavení se nepovedlo vygenerovat primární definiční sestavení.

  - Pokud přidáte odkazy na závislá sestavení, která nejsou sestaveními primární spolupráce, nemusíte vygenerovat primární definiční sestavení.

- Ruční vytváření sestavení primární spolupráce ve zdrojovém kódu pomocí jazyka, který je kompatibilní se specifikací CLS (Common Language Specification), jako je C#. Tento přístup je užitečný v případě, že knihovna typů není k dispozici.

Pro podepsání sestavení silným názvem musíte mít pár kryptografických klíčů. Podrobnosti najdete v tématu [Vytvoření páru klíčů](../../standard/assembly/create-public-private-key-pair.md).

### <a name="to-generate-a-primary-interop-assembly-using-tlbimpexe"></a>Generování primárního definičního sestavení pomocí Tlbimp.exe

1. Na příkazovém řádku zadejte:

    **Tlbimp** *tlbfile*  **/Primary/keyfile:** *filename* **/out:** *AssemblyName*

    V tomto příkazu je *tlbfile* soubor obsahující knihovnu typů modelu COM, název *souboru* je název kontejneru nebo souboru, který obsahuje dvojici klíčů, a *AssemblyName* je název sestavení pro podepsání silným názvem.

Primární spolupracující sestavení můžou odkazovat jenom na jiná primární spolupracující sestavení. Pokud vaše sestavení odkazuje na typy z knihovny typů modelu COM třetí strany, je nutné získat primární definiční sestavení od vydavatele před tím, než bude možné vygenerovat vaše primární definiční sestavení. Pokud jste Vydavatel, je nutné před generováním odkazujícího primárního sestavení vzájemné spolupráce vygenerovat primární definiční sestavení pro závislou knihovnu typů.

Závislé primární sestavení vzájemné spolupráce s číslem verze, které se liší od původní knihovny typů, není zjistitelné, když je nainstalován v aktuálním adresáři. Je nutné buď zaregistrovat závislé primární definiční sestavení v registru systému Windows, nebo můžete použít možnost **/reference** a ověřit, zda Tlbimp.exe najde závislou knihovnu DLL.

Můžete také zabalit více verzí knihovny typů. Pokyny najdete v tématu [Postup: zabalení více verzí knihoven typů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/1565h6hc(v=vs.100)).

## <a name="example"></a>Příklad

Následující příklad importuje knihovnu typů modelu COM `LibUtil.tlb` a podepíše sestavení `LibUtil.dll` se silným názvem pomocí souboru klíče `CompanyA.snk` . Vynecháte-li konkrétní název oboru názvů, tento příklad vytvoří výchozí obor názvů `LibUtil` .

```console
tlbimp LibUtil.tlb /primary /keyfile:CompanyA.snk /out:LibUtil.dll
```

Pro výstižnější název (pomocí *dodavatele*.* Název knihovny* – zásady pojmenování: v následujícím příkladu je popsán výchozí název souboru sestavení a název oboru názvů.

```console
tlbimp LibUtil.tlb /primary /keyfile:CompanyA.snk /namespace:CompanyA.LibUtil /out:CompanyA.LibUtil.dll
```

Následující příklad importuje `MyLib.tlb` , který odkazuje `CompanyA.LibUtil.dll` a podepíše sestavení `CompanyB.MyLib.dll` silným názvem pomocí souboru klíče `CompanyB.snk` . Obor názvů `CompanyB.MyLib` přepíše výchozí název oboru názvů.

```console
tlbimp MyLib.tlb /primary /keyfile:CompanyB.snk /namespace:CompanyB.MyLib /reference:CompanyA.LibUtil.dll /out:CompanyB.MyLib.dll
```

## <a name="see-also"></a>Viz také:

- [Postupy: Registrace primárních sestavení spolupráce](how-to-register-primary-interop-assemblies.md)
