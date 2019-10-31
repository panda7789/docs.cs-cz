---
title: 'Postupy: Registrace primárních sestavení spolupráce'
ms.date: 03/30/2017
helpviewer_keywords:
- registering primary interop assemblies
- primary interop assemblies, registering
ms.assetid: 4b2fcf8a-429d-43ce-8334-e026040be8bb
ms.openlocfilehash: c799e4ead2932f1c376a57488df30390ad48b90f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73107684"
---
# <a name="how-to-register-primary-interop-assemblies"></a>Postupy: Registrace primárních sestavení spolupráce

Třídy lze zařadit pouze pomocí zprostředkovatele komunikace s objekty COM a jsou vždy zařazeny jako rozhraní. V některých případech je rozhraní použité k zařazení třídy známé jako rozhraní třídy. Informace o přepsání rozhraní třídy s rozhraním dle vašeho výběru naleznete v tématu Obálka s možností připojení [modelu COM](../../standard/native-interop/com-callable-wrapper.md).

 I když jakýkoli vývojář, který chce použít typy COM z .NET Framework aplikace, může vygenerovat definiční sestavení. tím dojde k vytvoření problému. Pokaždé, když vývojář importuje a podepíše knihovnu typů modelu COM, tento Vývojář vytvoří sadu jedinečných typů, které jsou nekompatibilní s importovanými a podepsanými jiným vývojářem. Řešení tohoto problému s nekompatibilitou typů je pro každého vývojáře, aby získalo primární spolupracující sestavení pro dodavatele a podepsané.

 Pokud máte v úmyslu vystavovat typy COM třetích stran pro jiné aplikace, vždy použijte primární definiční sestavení poskytované stejným vydavatelem jako knihovna typů, kterou definuje. Kromě zajištění zaručené kompatibility typů jsou primární spolupracující sestavení často přizpůsobena dodavatelem za účelem vylepšení interoperability.

 I v případě, že neplánujete vystavovat typy modelu COM třetích stran, může použití primárního definičního sestavení zjednodušit úlohu vzájemného fungování komponent modelu COM. Tato strategie ale neposkytuje žádnou izolaci ze změn, které může dodavatel dělat pro typy definované v primárním definičním sestavení. Pokud vaše aplikace vyžaduje takovou izolaci, vygenerujte vlastní definiční sestavení namísto použití primárního definičního sestavení.

 Předtím, než je možné na ně odkazovat pomocí sady Visual Studio, je nutné zaregistrovat všechna získaná primární sestavení vzájemné spolupráce na vašem vývojovém počítači. Visual Studio hledá a použije primární definiční sestavení při prvním odkazování typu z knihovny typů modelu COM. Pokud Visual Studio nemůže najít primární definiční sestavení přidružené k knihovně typů, zobrazí se výzva k jeho získání nebo nabídce pro vytvoření sestavení vzájemné spolupráce. Nástroj pro [Import knihovny typů (Tlbimp. exe)](../tools/tlbimp-exe-type-library-importer.md) také používá registr k nalezení primárních sestavení vzájemné spolupráce.

 I když není nutné registrovat primární spolupracující sestavení, pokud plánujete použít Visual Studio, registrace poskytuje dvě výhody:

- Registrované primární sestavení vzájemné spolupráce je jasně označené pod klíčem registru původní knihovny typů. Registrace je nejlepším způsobem, jak najít primární definiční sestavení v počítači.

- Můžete se vyhnout nechtěnému generování a použití nového definičního sestavení, pokud v některých případech v budoucnu použijete aplikaci Visual Studio k odkazování na typ, pro který máte neregistrované primární spolupracující sestavení.

K registraci primárního definičního sestavení použijte [Nástroj pro registraci sestavení (Regasm. exe)](../tools/regasm-exe-assembly-registration-tool.md) .

## <a name="to-register-a-primary-interop-assembly"></a>Registrace primárního definičního sestavení

1. V příkazovém řádku zadejte příkaz:

     **Regasm** *AssemblyName*

     V tomto příkazu je *AssemblyName* název souboru registrovaného sestavení. Nástroj Regasm. exe přidá položku pro primární definiční sestavení pod stejným klíčem registru jako původní knihovnu typů.

## <a name="example"></a>Příklad
 Následující příklad registruje `CompanyA.UtilLib.dll` primární spolupracující sestavení.

```console
regasm CompanyA.UtilLib.dll
```

## <a name="see-also"></a>Viz také:

- [Programování s primárními definičními sestaveními](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/baxfadst(v=vs.100))
- [Hledání primárních sestavení vzájemné spolupráce](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/y06sxw56(v=vs.100))
- [Redistribuce primárních sestavení vzájemné spolupráce](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w0dt2w20(v=vs.100))
