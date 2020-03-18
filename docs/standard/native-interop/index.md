---
title: Nativní interoperabilita - .NET
description: Přečtěte si, jak komunikovat s nativními součástmi v rozhraní .NET.
ms.date: 01/18/2019
ms.openlocfilehash: 330466d74cc268214f74c4f575e6a2961f678972
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75706332"
---
# <a name="native-interoperability"></a>Nativní interoperabilita

Následující články ukazují různé způsoby provedení "nativní interoperability" v rozhraní .NET.

Existuje několik důvodů, proč byste chtěli volat do nativního kódu:

- Operační systémy jsou dodávány s velkým objemem api, které nejsou k dispozici v knihovnách spravovaných tříd. Ukázkovým příkladem tohoto scénáře by byl přístup k funkcím správy hardwaru nebo operačního systému.
- Komunikace s jinými součástmi, které mají nebo mohou vytvářet ABIs ve stylu C (nativní abis), jako je například kód Java, který je vystaven prostřednictvím [nativního rozhraní Java (JNI)](https://docs.oracle.com/javase/8/docs/technotes/guides/jni/) nebo jiného spravovaného jazyka, který by mohl vytvořit nativní součást.
- V systému Windows většina softwaru, který je nainstalován, například sada Microsoft Office, registruje komponenty modelu COM, které představují jejich programy, a umožňuje vývojářům je automatizovat nebo používat. To také vyžaduje nativní interoperabilitu.

Předchozí seznam nepokrývá všechny potenciální situace a scénáře, ve kterých by vývojář chtěl/ rád / potřeboval rozhraní s nativními součástmi. Knihovna tříd .NET například používá nativní podporu interoperability k implementaci slušného počtu svých rozhraní API, jako je podpora a manipulace konzoly, přístup k systému souborů a další. Je však důležité si uvědomit, že v případě potřeby existuje možnost.

> [!NOTE]
> Většina příkladů v této části bude prezentována pro všechny tři podporované platformy pro .NET Core (Windows, Linux a macOS). U některých krátkých a ilustrativních příkladů je však zobrazena pouze jedna ukázka, která používá názvy souborů systému Windows a rozšíření (tj. "dll" pro knihovny). To neznamená, že tyto funkce nejsou k dispozici na Linuxu nebo macOS, bylo to provedeno pouze pro pohodlí.

## <a name="see-also"></a>Viz také

- [Vyvolání platformy (P/Invoke)](pinvoke.md)
- [Zařazování typů](type-marshaling.md)
- [Nativní osvědčené postupy interoperability](best-practices.md)
