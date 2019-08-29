---
title: Nativní interoperabilita – .NET
description: Naučte se, jak používat nativní komponenty v .NET.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: 3ca213bc7228d2e4337607df2d47b334c5bea14f
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106808"
---
# <a name="native-interoperability"></a>Nativní interoperabilita

Následující články ukazují různé způsoby provádění "nativní interoperability" v rozhraní .NET.

Existuje několik důvodů, proč byste chtěli volat do nativního kódu:

- Operační systémy dodávají velké množství rozhraní API, která nejsou součástí knihoven spravované třídy. Hlavní příklad tohoto scénáře by byl přístup k funkcím správy hardwaru nebo operačního systému.
- Komunikace s dalšími komponentami, které mají nebo mohou vytvořit instrukce ABI ve stylu jazyka C (nativní instrukce ABI), jako je kód Java, který je zveřejněn prostřednictvím [rozhraní Java Native Interface (JNI)](https://docs.oracle.com/javase/8/docs/technotes/guides/jni/) nebo jakýkoli jiný spravovaný jazyk, který by mohl vytvořit nativní komponentu.
- Ve Windows většina softwaru, který se instaluje, jako je systém Microsoft Office sada, registruje komponenty modelu COM, které reprezentují své programy, a umožňuje vývojářům jejich automatizaci nebo použití. To také vyžaduje nativní interoperabilitu.

Předchozí seznam nepokrývá všechny možné situace a scénáře, ve kterých by měl vývojář chtít, aby mohl používat rozhraní s nativními součástmi. Knihovna tříd .NET, například používá nativní podporu interoperability k implementaci spravedlivého počtu jeho rozhraní API, jako je podpora konzoly a manipulace, přístup k systému souborů a další. Je ale důležité si uvědomit, že v případě potřeby máte možnost.

> [!NOTE]
> Většina příkladů v této části se zobrazí pro všechny tři podporované platformy pro .NET Core (Windows, Linux a macOS). V některých krátkých a ilustrativních příkladech se však zobrazí pouze jedna ukázka, která používá názvy souborů a rozšíření systému Windows (tj. "dll" pro knihovny). To neznamená, že tyto funkce nejsou k dispozici v systému Linux nebo macOS, ale byly provedeny pouze v zájmu usnadnění práce.

## <a name="see-also"></a>Viz také:

- [Vyvolání platformy (volání nespravovaného objektu)](pinvoke.md)
- [Zařazování typů](type-marshaling.md)
- [Nativní osvědčené postupy interoperability](best-practices.md)
