---
title: Přehled interoperability C# – Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- C# language, interoperability
- C++ Interop
- interoperability, about interoperability
- platform invoke
ms.assetid: c025b2e0-2357-4c27-8461-118f0090aeff
ms.openlocfilehash: 2c9eb2a8e6c2db8dc06ebe48ca6eb37d5cf638e7
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75700728"
---
# <a name="interoperability-overview-c-programming-guide"></a>Přehled interoperability (Průvodce programováním v C#)
Téma popisuje metody pro povolení interoperability mezi C# spravovaným kódem a nespravovaným kódem.  
  
## <a name="platform-invoke"></a>Vyvolání platformy  
 *Vyvolání platformy* je služba, která umožňuje spravovanému kódu volat nespravované funkce, které jsou implementované v knihovně DLL (Dynamic Link Library), například v rozhraní Microsoft Windows API. Vyhledá a vyvolá exportovanou funkci a zařadí argumenty (celá čísla, řetězce, pole, struktury atd.) v rámci hranice mezioperace podle potřeby.  
  
Další informace naleznete v tématu [spotřebovávání nespravovaných funkcí DLL](../../../framework/interop/consuming-unmanaged-dll-functions.md) a [použití vyvolání platformy k přehrání souboru WAV](./how-to-use-platform-invoke-to-play-a-wave-file.md).
  
> [!NOTE]
> Modul CLR ( [Common Language Runtime](../../../standard/clr.md) ) spravuje přístup k systémovým prostředkům. Volání nespravovaného kódu, který je mimo CLR, obchází tento mechanismus zabezpečení a proto představuje bezpečnostní riziko. Nespravovaný kód například může volat prostředky v nespravovaném kódu přímo, obejít mechanismy zabezpečení CLR. Další informace najdete v tématu [zabezpečení v .NET](../../../standard/security/index.md).  
  
## <a name="c-interop"></a>interoperabilita C++  
 Můžete použít C++ spolupráci, označovanou také jako pouze funguje (IJW), k zabalení nativní C++ třídy, aby ji bylo možné spotřebovat kódem, který je vytvořen v C# jiném .NET Frameworkovém jazyce. Chcete-li to provést, C++ napíšete kód pro zabalení NATIVNÍ knihovny DLL nebo komponenty modelu COM. Na rozdíl od jiných .NET Framework jazyků má C++ vizuál podporu interoperability, která umožňuje umístění spravovaného a nespravovaného kódu ve stejné aplikaci a dokonce i ve stejném souboru. Potom sestavíte C++ kód pomocí přepínače **/CLR** pro vytvoření spravovaného sestavení. Nakonec přidáte odkaz na sestavení v C# projektu a použijete zabalené objekty stejně, jako byste používali jiné spravované třídy.  
  
## <a name="exposing-com-components-to-c"></a>Vystavení komponent modelu COM pro C\#
 Komponentu modelu COM můžete využívat z C# projektu. Obecné kroky jsou následující:  
  
1. Vyhledejte komponentu modelu COM, kterou chcete použít, a zaregistrujte ji. K registraci nebo zrušení registrace knihovny COM použijte Regsvr32. exe.  
  
2. Přidejte do projektu odkaz na komponentu COM nebo knihovny typů.  
  
     Když přidáte odkaz, aplikace Visual Studio použije nástroj [Tlbimp. exe (importér knihovny typů)](../../../framework/tools/tlbimp-exe-type-library-importer.md), který jako vstup převezme knihovnu typů, a vytvoří tak výstup sestavení Interop .NET Framework. Sestavení, také pojmenované obálka RCW (Runtime), obsahuje spravované třídy a rozhraní, která zabalí třídy modelu COM a rozhraní, která jsou v knihovně typů. Visual Studio přidá do projektu odkaz na vygenerované sestavení.  
  
3. Vytvořte instanci třídy, která je definována v RCW. To zase vytvoří instanci objektu COM.  
  
4. Použijte objekt stejně jako ostatní spravované objekty. Když je objekt uvolněn uvolňováním paměti, instance objektu COM je také uvolněna z paměti.  
  
 Další informace najdete v tématu vystavení [komponent COM na .NET Framework](../../../framework/interop/exposing-com-components.md).  
  
## <a name="exposing-c-to-com"></a>Vystavení C# do modelu COM  
 Klienti modelu COM mohou C# využívat typy, které byly správně zpřístupněny. Základní kroky k vystavení C# typů jsou následující:  
  
1. Přidejte do C# projektu atributy spolupráce.  
  
     Model COM sestavení můžete zviditelnit úpravou vlastností vizuálního C# projektu. Další informace najdete v [dialogovém okně informace o sestavení](/visualstudio/ide/reference/assembly-information-dialog-box).  
  
2. Vygenerujte knihovnu typů modelu COM a zaregistrujte ji pro použití v modelu COM.  
  
     Můžete upravit vlastnosti vizuálního C# projektu a automaticky registrovat C# sestavení pro zprostředkovatele komunikace s objekty com. Visual Studio používá modul [Regasm. exe (Nástroj pro registraci sestavení)](../../../framework/tools/regasm-exe-assembly-registration-tool.md)s použitím přepínače příkazového řádku `/tlb`, který převezme spravované sestavení jako vstup, a vygeneruje knihovnu typů. Tato knihovna typů popisuje typy `public` v sestavení a přidává položky registru, aby klienti modelu COM mohli vytvořit spravované třídy.  
  
 Další informace najdete v tématu vystavení [.NET Framework komponent do modelu COM](../../../framework/interop/exposing-dotnet-components-to-com.md) a [Ukázkové třídy com](./example-com-class.md).  
  
## <a name="see-also"></a>Viz také:

- [Zlepšení výkonu spolupráce](https://docs.microsoft.com/previous-versions/msp-n-p/ff647812%28v=pandp.10%29)
- [Seznámení s interoperabilitou mezi COM a .NET](/office/client-developer/outlook/pia/introduction-to-interoperability-between-com-and-net)
- [Seznámení se zprostředkovatelem komunikace s objekty COM v Visual Basic](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)
- [Zařazování mezi spravovaným a nespravovaným kódem](../../../framework/interop/interop-marshaling.md)
- [Spolupráce s nespravovaným kódem](../../../framework/interop/index.md)
- [Průvodce programováním v jazyce C#](../index.md)
