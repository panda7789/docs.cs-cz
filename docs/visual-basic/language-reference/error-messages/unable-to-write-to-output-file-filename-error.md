---
title: "Nelze zapisovat do výstupního souboru '<filename>': <error>"
ms.date: 07/20/2015
f1_keywords:
- vbc31019
- bc31019
helpviewer_keywords:
- BC31019
ms.assetid: 0845b245-11bb-46fd-95ca-f6cef3c318ef
ms.openlocfilehash: 0f7580c53535c28c97213a5a0488c3fc0365c4ac
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55274102"
---
# <a name="unable-to-write-to-output-file-filename-error"></a><span data-ttu-id="b4a41-102">Nelze zapisovat do výstupního souboru '\<název souboru >': \<chyby ></span><span class="sxs-lookup"><span data-stu-id="b4a41-102">Unable to write to output file '\<filename>': \<error></span></span>
<span data-ttu-id="b4a41-103">Došlo k potížím, vytváření souboru.</span><span class="sxs-lookup"><span data-stu-id="b4a41-103">There was a problem creating the file.</span></span>  
  
 <span data-ttu-id="b4a41-104">Výstupní soubor nelze otevřít pro zápis.</span><span class="sxs-lookup"><span data-stu-id="b4a41-104">An output file cannot be opened for writing.</span></span> <span data-ttu-id="b4a41-105">Soubor (nebo na složku obsahující soubor) můžou být otevřené pro výhradní použití jiným procesem nebo je možné, že jeho nastaven atribut jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="b4a41-105">The file (or the folder containing the file) may be opened for exclusive use by another process, or it may have its read-only attribute set.</span></span>  
  
 <span data-ttu-id="b4a41-106">Běžné situace, kde je soubor otevřený výhradně jsou:</span><span class="sxs-lookup"><span data-stu-id="b4a41-106">Common situations where a file is opened exclusively are:</span></span>  
  
-   <span data-ttu-id="b4a41-107">Aplikace je již spuštěn a pomocí jeho soubory.</span><span class="sxs-lookup"><span data-stu-id="b4a41-107">The application is already running and using its files.</span></span> <span data-ttu-id="b4a41-108">Chcete-li tento problém vyřešit, ujistěte se, že aplikace není spuštěna.</span><span class="sxs-lookup"><span data-stu-id="b4a41-108">To solve this problem, make sure that the application is not running.</span></span>  
  
-   <span data-ttu-id="b4a41-109">Jiná aplikace má soubor otevřen.</span><span class="sxs-lookup"><span data-stu-id="b4a41-109">Another application has opened the file.</span></span> <span data-ttu-id="b4a41-110">Chcete-li tento problém vyřešit, ujistěte se, že žádná jiná aplikace je přístup k souborům.</span><span class="sxs-lookup"><span data-stu-id="b4a41-110">To solve this problem, make sure that no other application is accessing the files.</span></span> <span data-ttu-id="b4a41-111">Není vždy zřejmé aplikaci, pro kterou je přístupu k souborům; restartování počítače v takovém případě může být nejjednodušší způsob, jak aplikaci ukončit.</span><span class="sxs-lookup"><span data-stu-id="b4a41-111">It is not always obvious which application is accessing your files; in that case, restarting the computer might be the easiest way to terminate the application.</span></span>  
  
 <span data-ttu-id="b4a41-112">Pokud ani jeden z výstupních souborů projektu je označena jako jen pro čtení, tato výjimka bude vyvolána.</span><span class="sxs-lookup"><span data-stu-id="b4a41-112">If even one of the project output files is marked as read-only, this exception will be thrown.</span></span>  
  
 <span data-ttu-id="b4a41-113">**ID chyby:** BC31019</span><span class="sxs-lookup"><span data-stu-id="b4a41-113">**Error ID:** BC31019</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b4a41-114">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="b4a41-114">To correct this error</span></span>  
  
1.  <span data-ttu-id="b4a41-115">Kompilovat program znovu, abyste viděli, pokud se chyba objeví znovu.</span><span class="sxs-lookup"><span data-stu-id="b4a41-115">Compile the program again to see if the error recurs.</span></span>  
  
2.  <span data-ttu-id="b4a41-116">Pokud chyba přetrvává, uložte si práci a restartujte aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b4a41-116">If the error continues, save your work and restart Visual Studio.</span></span>  
  
3.  <span data-ttu-id="b4a41-117">Pokud chyba přetrvává, restartujte počítač.</span><span class="sxs-lookup"><span data-stu-id="b4a41-117">If the error continues, restart the computer.</span></span>  
  
4.  <span data-ttu-id="b4a41-118">Pokud se chyba objeví znovu, přeinstalujte Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b4a41-118">If the error recurs, reinstall Visual Basic.</span></span>  
  
5.  <span data-ttu-id="b4a41-119">Pokud chyba přetrvává po přeinstalaci, upozorní Microsoft Product Support Services.</span><span class="sxs-lookup"><span data-stu-id="b4a41-119">If the error persists after reinstallation, notify Microsoft Product Support Services.</span></span>  
  
### <a name="to-check-file-attributes-in-file-explorer"></a><span data-ttu-id="b4a41-120">Ke kontrole atributů souboru v Průzkumníku souborů</span><span class="sxs-lookup"><span data-stu-id="b4a41-120">To check file attributes in File Explorer</span></span>  
  
1.  <span data-ttu-id="b4a41-121">Otevřete složku, které vás zajímají.</span><span class="sxs-lookup"><span data-stu-id="b4a41-121">Open the folder you are interested in.</span></span>  
  
2.  <span data-ttu-id="b4a41-122">Klikněte na tlačítko **zobrazení** ikonu a zvolte **podrobnosti**.</span><span class="sxs-lookup"><span data-stu-id="b4a41-122">Click the **Views** icon and choose **Details**.</span></span>  
  
3.  <span data-ttu-id="b4a41-123">Klikněte pravým tlačítkem na záhlaví sloupce a vybrat **atributy** z rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="b4a41-123">Right-click the column header, and choose **Attributes** from the drop-down list.</span></span>  
  
### <a name="to-change-the-attributes-of-a-file-or-folder"></a><span data-ttu-id="b4a41-124">Chcete-li změnit atributy souboru nebo složky</span><span class="sxs-lookup"><span data-stu-id="b4a41-124">To change the attributes of a file or folder</span></span>  
  
1.  <span data-ttu-id="b4a41-125">V **Průzkumníka souborů**, klikněte pravým tlačítkem na soubor nebo složku a zvolte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="b4a41-125">In **File Explorer**, right-click the file or folder and choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="b4a41-126">V **atributy** část **Obecné** kartu, zrušte **jen pro čtení** pole.</span><span class="sxs-lookup"><span data-stu-id="b4a41-126">In the **Attributes** section of the **General** tab, clear the **Read-only** box.</span></span>  
  
3.  <span data-ttu-id="b4a41-127">Stisknutím klávesy **OK**.</span><span class="sxs-lookup"><span data-stu-id="b4a41-127">Press **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4a41-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b4a41-128">See also</span></span>
- [<span data-ttu-id="b4a41-129">Kontaktujte nás</span><span class="sxs-lookup"><span data-stu-id="b4a41-129">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
