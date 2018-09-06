---
title: Kolekce schémat ODBC
ms.date: 03/30/2017
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
ms.openlocfilehash: bdedbb11960f02b99dcca6388abf663635238f74
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43877528"
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="d5e8f-102">Kolekce schémat ODBC</span><span class="sxs-lookup"><span data-stu-id="d5e8f-102">ODBC Schema Collections</span></span>
<span data-ttu-id="d5e8f-103">Tato část popisuje kolekci podpora schématu pro ovladače ODBC pro Microsoft SQL Server, Oracle a Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="d5e8f-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="d5e8f-104">Ovladač ODBC Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="d5e8f-104">Microsoft SQL Server ODBC Driver</span></span>  
 <span data-ttu-id="d5e8f-105">Ovladače ODBC Microsoft SQL Server podporuje následující kolekce určité schéma kromě společné kolekce schémat:</span><span class="sxs-lookup"><span data-stu-id="d5e8f-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="d5e8f-106">Tabulky</span><span class="sxs-lookup"><span data-stu-id="d5e8f-106">Tables</span></span>  
  
-   <span data-ttu-id="d5e8f-107">Indexy</span><span class="sxs-lookup"><span data-stu-id="d5e8f-107">Indexes</span></span>  
  
-   <span data-ttu-id="d5e8f-108">Sloupce</span><span class="sxs-lookup"><span data-stu-id="d5e8f-108">Columns</span></span>  
  
-   <span data-ttu-id="d5e8f-109">Procedury</span><span class="sxs-lookup"><span data-stu-id="d5e8f-109">Procedures</span></span>  
  
-   <span data-ttu-id="d5e8f-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="d5e8f-110">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="d5e8f-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="d5e8f-111">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="d5e8f-112">Zobrazení</span><span class="sxs-lookup"><span data-stu-id="d5e8f-112">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="d5e8f-113">Tabulky a zobrazení</span><span class="sxs-lookup"><span data-stu-id="d5e8f-113">Tables and Views</span></span>  
  
|<span data-ttu-id="d5e8f-114">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="d5e8f-114">ColumnName</span></span>|<span data-ttu-id="d5e8f-115">Datový typ</span><span class="sxs-lookup"><span data-stu-id="d5e8f-115">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d5e8f-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="d5e8f-116">TABLE_CAT</span></span>|<span data-ttu-id="d5e8f-117">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-117">String</span></span>|  
|<span data-ttu-id="d5e8f-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="d5e8f-118">TABLE_SCHEM</span></span>|<span data-ttu-id="d5e8f-119">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-119">String</span></span>|  
|<span data-ttu-id="d5e8f-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d5e8f-120">TABLE_NAME</span></span>|<span data-ttu-id="d5e8f-121">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-121">String</span></span>|  
|<span data-ttu-id="d5e8f-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="d5e8f-122">TABLE_TYPE</span></span>|<span data-ttu-id="d5e8f-123">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-123">String</span></span>|  
|<span data-ttu-id="d5e8f-124">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="d5e8f-124">REMARKS</span></span>|<span data-ttu-id="d5e8f-125">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-125">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="d5e8f-126">Indexy</span><span class="sxs-lookup"><span data-stu-id="d5e8f-126">Indexes</span></span>  
  
|<span data-ttu-id="d5e8f-127">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="d5e8f-127">ColumnName</span></span>|<span data-ttu-id="d5e8f-128">Datový typ</span><span class="sxs-lookup"><span data-stu-id="d5e8f-128">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d5e8f-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="d5e8f-129">TABLE_CAT</span></span>|<span data-ttu-id="d5e8f-130">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-130">String</span></span>|  
|<span data-ttu-id="d5e8f-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="d5e8f-131">TABLE_SCHEM</span></span>|<span data-ttu-id="d5e8f-132">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-132">String</span></span>|  
|<span data-ttu-id="d5e8f-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d5e8f-133">TABLE_NAME</span></span>|<span data-ttu-id="d5e8f-134">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-134">String</span></span>|  
|<span data-ttu-id="d5e8f-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="d5e8f-135">NON_UNIQUE</span></span>|<span data-ttu-id="d5e8f-136">Int16</span><span class="sxs-lookup"><span data-stu-id="d5e8f-136">Int16</span></span>|  
|<span data-ttu-id="d5e8f-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="d5e8f-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="d5e8f-138">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-138">String</span></span>|  
|<span data-ttu-id="d5e8f-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="d5e8f-139">INDEX_NAME</span></span>|<span data-ttu-id="d5e8f-140">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-140">String</span></span>|  
|<span data-ttu-id="d5e8f-141">TYP</span><span class="sxs-lookup"><span data-stu-id="d5e8f-141">TYPE</span></span>|<span data-ttu-id="d5e8f-142">Int16</span><span class="sxs-lookup"><span data-stu-id="d5e8f-142">Int16</span></span>|  
|<span data-ttu-id="d5e8f-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="d5e8f-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="d5e8f-144">Int16</span><span class="sxs-lookup"><span data-stu-id="d5e8f-144">Int16</span></span>|  
|<span data-ttu-id="d5e8f-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="d5e8f-145">COLUMN_NAME</span></span>|<span data-ttu-id="d5e8f-146">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-146">String</span></span>|  
|<span data-ttu-id="d5e8f-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="d5e8f-147">ASC_OR_DESC</span></span>|<span data-ttu-id="d5e8f-148">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-148">String</span></span>|  
|<span data-ttu-id="d5e8f-149">CARDINATLITY</span><span class="sxs-lookup"><span data-stu-id="d5e8f-149">CARDINATLITY</span></span>|<span data-ttu-id="d5e8f-150">Int32</span><span class="sxs-lookup"><span data-stu-id="d5e8f-150">Int32</span></span>|  
|<span data-ttu-id="d5e8f-151">STRÁNKY</span><span class="sxs-lookup"><span data-stu-id="d5e8f-151">PAGES</span></span>|<span data-ttu-id="d5e8f-152">Int32</span><span class="sxs-lookup"><span data-stu-id="d5e8f-152">Int32</span></span>|  
|<span data-ttu-id="d5e8f-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="d5e8f-153">FILTER_CONDITION</span></span>|<span data-ttu-id="d5e8f-154">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-154">String</span></span>|  
|<span data-ttu-id="d5e8f-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d5e8f-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="d5e8f-156">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-156">String</span></span>|  
|<span data-ttu-id="d5e8f-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="d5e8f-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="d5e8f-158">Byte</span><span class="sxs-lookup"><span data-stu-id="d5e8f-158">Byte</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="d5e8f-159">Sloupce</span><span class="sxs-lookup"><span data-stu-id="d5e8f-159">Columns</span></span>  
  
|<span data-ttu-id="d5e8f-160">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="d5e8f-160">ColumnName</span></span>|<span data-ttu-id="d5e8f-161">Datový typ</span><span class="sxs-lookup"><span data-stu-id="d5e8f-161">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d5e8f-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="d5e8f-162">TABLE_CAT</span></span>|<span data-ttu-id="d5e8f-163">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-163">String</span></span>|  
|<span data-ttu-id="d5e8f-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="d5e8f-164">TABLE_SCHEM</span></span>|<span data-ttu-id="d5e8f-165">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-165">String</span></span>|  
|<span data-ttu-id="d5e8f-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d5e8f-166">TABLE_NAME</span></span>|<span data-ttu-id="d5e8f-167">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-167">String</span></span>|  
|<span data-ttu-id="d5e8f-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="d5e8f-168">COLUMN_NAME</span></span>|<span data-ttu-id="d5e8f-169">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-169">String</span></span>|  
|<span data-ttu-id="d5e8f-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="d5e8f-170">DATA_TYPE</span></span>|<span data-ttu-id="d5e8f-171">Int16</span><span class="sxs-lookup"><span data-stu-id="d5e8f-171">Int16</span></span>|  
|<span data-ttu-id="d5e8f-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="d5e8f-172">TYPE_NAME</span></span>|<span data-ttu-id="d5e8f-173">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-173">String</span></span>|  
|<span data-ttu-id="d5e8f-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="d5e8f-174">COLUMN_SIZE</span></span>|<span data-ttu-id="d5e8f-175">Int32</span><span class="sxs-lookup"><span data-stu-id="d5e8f-175">Int32</span></span>|  
|<span data-ttu-id="d5e8f-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="d5e8f-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="d5e8f-177">Int32</span><span class="sxs-lookup"><span data-stu-id="d5e8f-177">Int32</span></span>|  
|<span data-ttu-id="d5e8f-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="d5e8f-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="d5e8f-179">Int16</span><span class="sxs-lookup"><span data-stu-id="d5e8f-179">Int16</span></span>|  
|<span data-ttu-id="d5e8f-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="d5e8f-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="d5e8f-181">Int16</span><span class="sxs-lookup"><span data-stu-id="d5e8f-181">Int16</span></span>|  
|<span data-ttu-id="d5e8f-182">S POVOLENOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="d5e8f-182">NULLABLE</span></span>|<span data-ttu-id="d5e8f-183">Int16</span><span class="sxs-lookup"><span data-stu-id="d5e8f-183">Int16</span></span>|  
|<span data-ttu-id="d5e8f-184">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="d5e8f-184">REMARKS</span></span>|<span data-ttu-id="d5e8f-185">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-185">String</span></span>|  
|<span data-ttu-id="d5e8f-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="d5e8f-186">COLUMN_DEF</span></span>|<span data-ttu-id="d5e8f-187">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-187">String</span></span>|  
|<span data-ttu-id="d5e8f-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="d5e8f-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="d5e8f-189">Int16</span><span class="sxs-lookup"><span data-stu-id="d5e8f-189">Int16</span></span>|  
|<span data-ttu-id="d5e8f-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="d5e8f-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="d5e8f-191">Int16</span><span class="sxs-lookup"><span data-stu-id="d5e8f-191">Int16</span></span>|  
|<span data-ttu-id="d5e8f-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="d5e8f-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="d5e8f-193">Int32</span><span class="sxs-lookup"><span data-stu-id="d5e8f-193">Int32</span></span>|  
|<span data-ttu-id="d5e8f-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="d5e8f-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="d5e8f-195">Int32</span><span class="sxs-lookup"><span data-stu-id="d5e8f-195">Int32</span></span>|  
|<span data-ttu-id="d5e8f-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="d5e8f-196">IS_NULLABLE</span></span>|<span data-ttu-id="d5e8f-197">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-197">String</span></span>|  
|<span data-ttu-id="d5e8f-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d5e8f-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="d5e8f-199">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-199">String</span></span>|  
|<span data-ttu-id="d5e8f-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d5e8f-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="d5e8f-201">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-201">String</span></span>|  
|<span data-ttu-id="d5e8f-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="d5e8f-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="d5e8f-203">Byte</span><span class="sxs-lookup"><span data-stu-id="d5e8f-203">Byte</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="d5e8f-204">Procedury</span><span class="sxs-lookup"><span data-stu-id="d5e8f-204">Procedures</span></span>  
  
|<span data-ttu-id="d5e8f-205">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="d5e8f-205">ColumnName</span></span>|<span data-ttu-id="d5e8f-206">Datový typ</span><span class="sxs-lookup"><span data-stu-id="d5e8f-206">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d5e8f-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="d5e8f-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="d5e8f-208">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-208">String</span></span>|  
|<span data-ttu-id="d5e8f-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="d5e8f-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="d5e8f-210">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-210">String</span></span>|  
|<span data-ttu-id="d5e8f-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="d5e8f-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="d5e8f-212">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-212">String</span></span>|  
|<span data-ttu-id="d5e8f-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="d5e8f-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="d5e8f-214">Int32</span><span class="sxs-lookup"><span data-stu-id="d5e8f-214">Int32</span></span>|  
|<span data-ttu-id="d5e8f-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="d5e8f-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="d5e8f-216">Int32</span><span class="sxs-lookup"><span data-stu-id="d5e8f-216">Int32</span></span>|  
|<span data-ttu-id="d5e8f-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="d5e8f-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="d5e8f-218">Int32</span><span class="sxs-lookup"><span data-stu-id="d5e8f-218">Int32</span></span>|  
|<span data-ttu-id="d5e8f-219">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="d5e8f-219">REMARKS</span></span>|<span data-ttu-id="d5e8f-220">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-220">String</span></span>|  
|<span data-ttu-id="d5e8f-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="d5e8f-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="d5e8f-222">Int16</span><span class="sxs-lookup"><span data-stu-id="d5e8f-222">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="d5e8f-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="d5e8f-223">ProcedureColumns</span></span>  
  
|<span data-ttu-id="d5e8f-224">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="d5e8f-224">ColumnName</span></span>|<span data-ttu-id="d5e8f-225">Datový typ</span><span class="sxs-lookup"><span data-stu-id="d5e8f-225">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d5e8f-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="d5e8f-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="d5e8f-227">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-227">String</span></span>|  
|<span data-ttu-id="d5e8f-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="d5e8f-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="d5e8f-229">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-229">String</span></span>|  
|<span data-ttu-id="d5e8f-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="d5e8f-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="d5e8f-231">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-231">String</span></span>|  
|<span data-ttu-id="d5e8f-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="d5e8f-232">COLUMN_NAME</span></span>|<span data-ttu-id="d5e8f-233">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-233">String</span></span>|  
|<span data-ttu-id="d5e8f-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="d5e8f-234">COLUMN_TYPE</span></span>|<span data-ttu-id="d5e8f-235">Int16</span><span class="sxs-lookup"><span data-stu-id="d5e8f-235">Int16</span></span>|  
|<span data-ttu-id="d5e8f-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="d5e8f-236">DATA_TYPE</span></span>|<span data-ttu-id="d5e8f-237">Int16</span><span class="sxs-lookup"><span data-stu-id="d5e8f-237">Int16</span></span>|  
|<span data-ttu-id="d5e8f-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="d5e8f-238">TYPE_NAME</span></span>|<span data-ttu-id="d5e8f-239">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-239">String</span></span>|  
|<span data-ttu-id="d5e8f-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="d5e8f-240">COLUMN_SIZE</span></span>|<span data-ttu-id="d5e8f-241">Int32</span><span class="sxs-lookup"><span data-stu-id="d5e8f-241">Int32</span></span>|  
|<span data-ttu-id="d5e8f-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="d5e8f-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="d5e8f-243">Int32</span><span class="sxs-lookup"><span data-stu-id="d5e8f-243">Int32</span></span>|  
|<span data-ttu-id="d5e8f-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="d5e8f-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="d5e8f-245">Int16</span><span class="sxs-lookup"><span data-stu-id="d5e8f-245">Int16</span></span>|  
|<span data-ttu-id="d5e8f-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="d5e8f-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="d5e8f-247">Int16</span><span class="sxs-lookup"><span data-stu-id="d5e8f-247">Int16</span></span>|  
|<span data-ttu-id="d5e8f-248">S POVOLENOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="d5e8f-248">NULLABLE</span></span>|<span data-ttu-id="d5e8f-249">Int16</span><span class="sxs-lookup"><span data-stu-id="d5e8f-249">Int16</span></span>|  
|<span data-ttu-id="d5e8f-250">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="d5e8f-250">REMARKS</span></span>|<span data-ttu-id="d5e8f-251">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-251">String</span></span>|  
|<span data-ttu-id="d5e8f-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="d5e8f-252">COLUMN_DEF</span></span>|<span data-ttu-id="d5e8f-253">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-253">String</span></span>|  
|<span data-ttu-id="d5e8f-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="d5e8f-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="d5e8f-255">Int16</span><span class="sxs-lookup"><span data-stu-id="d5e8f-255">Int16</span></span>|  
|<span data-ttu-id="d5e8f-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="d5e8f-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="d5e8f-257">Int16</span><span class="sxs-lookup"><span data-stu-id="d5e8f-257">Int16</span></span>|  
|<span data-ttu-id="d5e8f-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="d5e8f-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="d5e8f-259">Int32</span><span class="sxs-lookup"><span data-stu-id="d5e8f-259">Int32</span></span>|  
|<span data-ttu-id="d5e8f-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="d5e8f-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="d5e8f-261">Int32</span><span class="sxs-lookup"><span data-stu-id="d5e8f-261">Int32</span></span>|  
|<span data-ttu-id="d5e8f-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="d5e8f-262">IS_NULLABLE</span></span>|<span data-ttu-id="d5e8f-263">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-263">String</span></span>|  
|<span data-ttu-id="d5e8f-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d5e8f-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="d5e8f-265">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-265">String</span></span>|  
|<span data-ttu-id="d5e8f-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d5e8f-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="d5e8f-267">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-267">String</span></span>|  
|<span data-ttu-id="d5e8f-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="d5e8f-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="d5e8f-269">Byte</span><span class="sxs-lookup"><span data-stu-id="d5e8f-269">Byte</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="d5e8f-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="d5e8f-270">ProcedureParameters</span></span>  
  
|<span data-ttu-id="d5e8f-271">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="d5e8f-271">ColumnName</span></span>|<span data-ttu-id="d5e8f-272">Datový typ</span><span class="sxs-lookup"><span data-stu-id="d5e8f-272">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d5e8f-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="d5e8f-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="d5e8f-274">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-274">String</span></span>|  
|<span data-ttu-id="d5e8f-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="d5e8f-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="d5e8f-276">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-276">String</span></span>|  
|<span data-ttu-id="d5e8f-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="d5e8f-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="d5e8f-278">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-278">String</span></span>|  
|<span data-ttu-id="d5e8f-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="d5e8f-279">COLUMN_NAME</span></span>|<span data-ttu-id="d5e8f-280">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-280">String</span></span>|  
|<span data-ttu-id="d5e8f-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="d5e8f-281">COLUMN_TYPE</span></span>|<span data-ttu-id="d5e8f-282">Int16</span><span class="sxs-lookup"><span data-stu-id="d5e8f-282">Int16</span></span>|  
|<span data-ttu-id="d5e8f-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="d5e8f-283">DATA_TYPE</span></span>|<span data-ttu-id="d5e8f-284">Int16</span><span class="sxs-lookup"><span data-stu-id="d5e8f-284">Int16</span></span>|  
|<span data-ttu-id="d5e8f-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="d5e8f-285">TYPE_NAME</span></span>|<span data-ttu-id="d5e8f-286">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-286">String</span></span>|  
|<span data-ttu-id="d5e8f-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="d5e8f-287">COLUMN_SIZE</span></span>|<span data-ttu-id="d5e8f-288">Int32</span><span class="sxs-lookup"><span data-stu-id="d5e8f-288">Int32</span></span>|  
|<span data-ttu-id="d5e8f-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="d5e8f-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="d5e8f-290">Int32</span><span class="sxs-lookup"><span data-stu-id="d5e8f-290">Int32</span></span>|  
|<span data-ttu-id="d5e8f-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="d5e8f-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="d5e8f-292">Int16</span><span class="sxs-lookup"><span data-stu-id="d5e8f-292">Int16</span></span>|  
|<span data-ttu-id="d5e8f-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="d5e8f-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="d5e8f-294">Int16</span><span class="sxs-lookup"><span data-stu-id="d5e8f-294">Int16</span></span>|  
|<span data-ttu-id="d5e8f-295">S POVOLENOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="d5e8f-295">NULLABLE</span></span>|<span data-ttu-id="d5e8f-296">Int16</span><span class="sxs-lookup"><span data-stu-id="d5e8f-296">Int16</span></span>|  
|<span data-ttu-id="d5e8f-297">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="d5e8f-297">REMARKS</span></span>|<span data-ttu-id="d5e8f-298">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-298">String</span></span>|  
|<span data-ttu-id="d5e8f-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="d5e8f-299">COLUMN_DEF</span></span>|<span data-ttu-id="d5e8f-300">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-300">String</span></span>|  
|<span data-ttu-id="d5e8f-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="d5e8f-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="d5e8f-302">Int16</span><span class="sxs-lookup"><span data-stu-id="d5e8f-302">Int16</span></span>|  
|<span data-ttu-id="d5e8f-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="d5e8f-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="d5e8f-304">Int16</span><span class="sxs-lookup"><span data-stu-id="d5e8f-304">Int16</span></span>|  
|<span data-ttu-id="d5e8f-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="d5e8f-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="d5e8f-306">Int32</span><span class="sxs-lookup"><span data-stu-id="d5e8f-306">Int32</span></span>|  
|<span data-ttu-id="d5e8f-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="d5e8f-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="d5e8f-308">Int32</span><span class="sxs-lookup"><span data-stu-id="d5e8f-308">Int32</span></span>|  
|<span data-ttu-id="d5e8f-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="d5e8f-309">IS_NULLABLE</span></span>|<span data-ttu-id="d5e8f-310">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-310">String</span></span>|  
|<span data-ttu-id="d5e8f-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d5e8f-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="d5e8f-312">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-312">String</span></span>|  
|<span data-ttu-id="d5e8f-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d5e8f-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="d5e8f-314">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-314">String</span></span>|  
|<span data-ttu-id="d5e8f-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="d5e8f-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="d5e8f-316">Byte</span><span class="sxs-lookup"><span data-stu-id="d5e8f-316">Byte</span></span>|  
  
## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="d5e8f-317">Ovladač ODBC Microsoft Oracle</span><span class="sxs-lookup"><span data-stu-id="d5e8f-317">Microsoft Oracle ODBC Driver</span></span>  
 <span data-ttu-id="d5e8f-318">Ovladače ODBC Microsoft SQL Server Oracle podporuje následující kolekce určité schéma kromě společné kolekce schémat:</span><span class="sxs-lookup"><span data-stu-id="d5e8f-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="d5e8f-319">Tabulky</span><span class="sxs-lookup"><span data-stu-id="d5e8f-319">Tables</span></span>  
  
-   <span data-ttu-id="d5e8f-320">Sloupce</span><span class="sxs-lookup"><span data-stu-id="d5e8f-320">Columns</span></span>  
  
-   <span data-ttu-id="d5e8f-321">Procedury</span><span class="sxs-lookup"><span data-stu-id="d5e8f-321">Procedures</span></span>  
  
-   <span data-ttu-id="d5e8f-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="d5e8f-322">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="d5e8f-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="d5e8f-323">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="d5e8f-324">Zobrazení</span><span class="sxs-lookup"><span data-stu-id="d5e8f-324">Views</span></span>  
  
-   <span data-ttu-id="d5e8f-325">Indexy</span><span class="sxs-lookup"><span data-stu-id="d5e8f-325">Indexes</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="d5e8f-326">Tabulky a zobrazení</span><span class="sxs-lookup"><span data-stu-id="d5e8f-326">Tables and Views</span></span>  
  
|<span data-ttu-id="d5e8f-327">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="d5e8f-327">ColumnName</span></span>|<span data-ttu-id="d5e8f-328">Datový typ</span><span class="sxs-lookup"><span data-stu-id="d5e8f-328">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d5e8f-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="d5e8f-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="d5e8f-330">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-330">String</span></span>|  
|<span data-ttu-id="d5e8f-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="d5e8f-331">TABLE_OWNER</span></span>|<span data-ttu-id="d5e8f-332">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-332">String</span></span>|  
|<span data-ttu-id="d5e8f-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d5e8f-333">TABLE_NAME</span></span>|<span data-ttu-id="d5e8f-334">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-334">String</span></span>|  
|<span data-ttu-id="d5e8f-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="d5e8f-335">TABLE_TYPE</span></span>|<span data-ttu-id="d5e8f-336">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-336">String</span></span>|  
|<span data-ttu-id="d5e8f-337">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="d5e8f-337">REMARKS</span></span>|<span data-ttu-id="d5e8f-338">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-338">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="d5e8f-339">Sloupce</span><span class="sxs-lookup"><span data-stu-id="d5e8f-339">Columns</span></span>  
  
|<span data-ttu-id="d5e8f-340">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="d5e8f-340">ColumnName</span></span>|<span data-ttu-id="d5e8f-341">Datový typ</span><span class="sxs-lookup"><span data-stu-id="d5e8f-341">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d5e8f-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="d5e8f-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="d5e8f-343">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-343">String</span></span>|  
|<span data-ttu-id="d5e8f-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="d5e8f-344">TABLE_OWNER</span></span>|<span data-ttu-id="d5e8f-345">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-345">String</span></span>|  
|<span data-ttu-id="d5e8f-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d5e8f-346">TABLE_NAME</span></span>|<span data-ttu-id="d5e8f-347">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-347">String</span></span>|  
|<span data-ttu-id="d5e8f-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="d5e8f-348">COLUMN_NAME</span></span>|<span data-ttu-id="d5e8f-349">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-349">String</span></span>|  
|<span data-ttu-id="d5e8f-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="d5e8f-350">DATA_TYPE</span></span>|<span data-ttu-id="d5e8f-351">Int16</span><span class="sxs-lookup"><span data-stu-id="d5e8f-351">Int16</span></span>|  
|<span data-ttu-id="d5e8f-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="d5e8f-352">TYPE_NAME</span></span>|<span data-ttu-id="d5e8f-353">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-353">String</span></span>|  
|<span data-ttu-id="d5e8f-354">PŘESNOST</span><span class="sxs-lookup"><span data-stu-id="d5e8f-354">PRECISION</span></span>|<span data-ttu-id="d5e8f-355">Int32</span><span class="sxs-lookup"><span data-stu-id="d5e8f-355">Int32</span></span>|  
|<span data-ttu-id="d5e8f-356">DÉLKA</span><span class="sxs-lookup"><span data-stu-id="d5e8f-356">LENGTH</span></span>|<span data-ttu-id="d5e8f-357">Int32</span><span class="sxs-lookup"><span data-stu-id="d5e8f-357">Int32</span></span>|  
|<span data-ttu-id="d5e8f-358">ŠKÁLOVÁNÍ</span><span class="sxs-lookup"><span data-stu-id="d5e8f-358">SCALE</span></span>|<span data-ttu-id="d5e8f-359">Int16</span><span class="sxs-lookup"><span data-stu-id="d5e8f-359">Int16</span></span>|  
|<span data-ttu-id="d5e8f-360">RADIX</span><span class="sxs-lookup"><span data-stu-id="d5e8f-360">RADIX</span></span>|<span data-ttu-id="d5e8f-361">Int16</span><span class="sxs-lookup"><span data-stu-id="d5e8f-361">Int16</span></span>|  
|<span data-ttu-id="d5e8f-362">S POVOLENOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="d5e8f-362">NULLABLE</span></span>|<span data-ttu-id="d5e8f-363">Int16</span><span class="sxs-lookup"><span data-stu-id="d5e8f-363">Int16</span></span>|  
|<span data-ttu-id="d5e8f-364">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="d5e8f-364">REMARKS</span></span>|<span data-ttu-id="d5e8f-365">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-365">String</span></span>|  
|<span data-ttu-id="d5e8f-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="d5e8f-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="d5e8f-367">Int32</span><span class="sxs-lookup"><span data-stu-id="d5e8f-367">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="d5e8f-368">Procedury</span><span class="sxs-lookup"><span data-stu-id="d5e8f-368">Procedures</span></span>  
  
|<span data-ttu-id="d5e8f-369">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="d5e8f-369">ColumnName</span></span>|<span data-ttu-id="d5e8f-370">Datový typ</span><span class="sxs-lookup"><span data-stu-id="d5e8f-370">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d5e8f-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="d5e8f-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="d5e8f-372">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-372">String</span></span>|  
|<span data-ttu-id="d5e8f-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="d5e8f-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="d5e8f-374">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-374">String</span></span>|  
|<span data-ttu-id="d5e8f-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="d5e8f-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="d5e8f-376">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-376">String</span></span>|  
|<span data-ttu-id="d5e8f-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="d5e8f-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="d5e8f-378">Int16</span><span class="sxs-lookup"><span data-stu-id="d5e8f-378">Int16</span></span>|  
|<span data-ttu-id="d5e8f-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="d5e8f-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="d5e8f-380">Int16</span><span class="sxs-lookup"><span data-stu-id="d5e8f-380">Int16</span></span>|  
|<span data-ttu-id="d5e8f-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="d5e8f-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="d5e8f-382">Int16</span><span class="sxs-lookup"><span data-stu-id="d5e8f-382">Int16</span></span>|  
|<span data-ttu-id="d5e8f-383">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="d5e8f-383">REMARKS</span></span>|<span data-ttu-id="d5e8f-384">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-384">String</span></span>|  
|<span data-ttu-id="d5e8f-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="d5e8f-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="d5e8f-386">Int16</span><span class="sxs-lookup"><span data-stu-id="d5e8f-386">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="d5e8f-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="d5e8f-387">ProcedureColumns</span></span>  
  
|<span data-ttu-id="d5e8f-388">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="d5e8f-388">ColumnName</span></span>|<span data-ttu-id="d5e8f-389">Datový typ</span><span class="sxs-lookup"><span data-stu-id="d5e8f-389">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d5e8f-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="d5e8f-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="d5e8f-391">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-391">String</span></span>|  
|<span data-ttu-id="d5e8f-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="d5e8f-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="d5e8f-393">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-393">String</span></span>|  
|<span data-ttu-id="d5e8f-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="d5e8f-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="d5e8f-395">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-395">String</span></span>|  
|<span data-ttu-id="d5e8f-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="d5e8f-396">COLUMN_NAME</span></span>|<span data-ttu-id="d5e8f-397">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-397">String</span></span>|  
|<span data-ttu-id="d5e8f-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="d5e8f-398">COLUMN_TYPE</span></span>|<span data-ttu-id="d5e8f-399">Int16</span><span class="sxs-lookup"><span data-stu-id="d5e8f-399">Int16</span></span>|  
|<span data-ttu-id="d5e8f-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="d5e8f-400">DATA_TYPE</span></span>|<span data-ttu-id="d5e8f-401">Int16</span><span class="sxs-lookup"><span data-stu-id="d5e8f-401">Int16</span></span>|  
|<span data-ttu-id="d5e8f-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="d5e8f-402">TYPE_NAME</span></span>|<span data-ttu-id="d5e8f-403">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-403">String</span></span>|  
|<span data-ttu-id="d5e8f-404">PŘESNOST</span><span class="sxs-lookup"><span data-stu-id="d5e8f-404">PRECISION</span></span>|<span data-ttu-id="d5e8f-405">Int32</span><span class="sxs-lookup"><span data-stu-id="d5e8f-405">Int32</span></span>|  
|<span data-ttu-id="d5e8f-406">DÉLKA</span><span class="sxs-lookup"><span data-stu-id="d5e8f-406">LENGTH</span></span>|<span data-ttu-id="d5e8f-407">Int32</span><span class="sxs-lookup"><span data-stu-id="d5e8f-407">Int32</span></span>|  
|<span data-ttu-id="d5e8f-408">ŠKÁLOVÁNÍ</span><span class="sxs-lookup"><span data-stu-id="d5e8f-408">SCALE</span></span>|<span data-ttu-id="d5e8f-409">Int16</span><span class="sxs-lookup"><span data-stu-id="d5e8f-409">Int16</span></span>|  
|<span data-ttu-id="d5e8f-410">RADIX</span><span class="sxs-lookup"><span data-stu-id="d5e8f-410">RADIX</span></span>|<span data-ttu-id="d5e8f-411">Int16</span><span class="sxs-lookup"><span data-stu-id="d5e8f-411">Int16</span></span>|  
|<span data-ttu-id="d5e8f-412">S POVOLENOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="d5e8f-412">NULLABLE</span></span>|<span data-ttu-id="d5e8f-413">Int16</span><span class="sxs-lookup"><span data-stu-id="d5e8f-413">Int16</span></span>|  
|<span data-ttu-id="d5e8f-414">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="d5e8f-414">REMARKS</span></span>|<span data-ttu-id="d5e8f-415">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-415">String</span></span>|  
|<span data-ttu-id="d5e8f-416">PŘETÍŽENÍ</span><span class="sxs-lookup"><span data-stu-id="d5e8f-416">OVERLOAD</span></span>|<span data-ttu-id="d5e8f-417">Int32</span><span class="sxs-lookup"><span data-stu-id="d5e8f-417">Int32</span></span>|  
|<span data-ttu-id="d5e8f-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="d5e8f-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="d5e8f-419">Int32</span><span class="sxs-lookup"><span data-stu-id="d5e8f-419">Int32</span></span>|  
  
## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="d5e8f-420">Ovladač ODBC Microsoft Jet</span><span class="sxs-lookup"><span data-stu-id="d5e8f-420">Microsoft Jet ODBC Driver</span></span>  
 <span data-ttu-id="d5e8f-421">Ovladač ODBC Microsoft Jet podporuje následující kolekce určité schéma kromě společné kolekce schémat:</span><span class="sxs-lookup"><span data-stu-id="d5e8f-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="d5e8f-422">Tabulky</span><span class="sxs-lookup"><span data-stu-id="d5e8f-422">Tables</span></span>  
  
-   <span data-ttu-id="d5e8f-423">Indexy</span><span class="sxs-lookup"><span data-stu-id="d5e8f-423">Indexes</span></span>  
  
-   <span data-ttu-id="d5e8f-424">Sloupce</span><span class="sxs-lookup"><span data-stu-id="d5e8f-424">Columns</span></span>  
  
-   <span data-ttu-id="d5e8f-425">Procedury</span><span class="sxs-lookup"><span data-stu-id="d5e8f-425">Procedures</span></span>  
  
-   <span data-ttu-id="d5e8f-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="d5e8f-426">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="d5e8f-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="d5e8f-427">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="d5e8f-428">Zobrazení</span><span class="sxs-lookup"><span data-stu-id="d5e8f-428">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="d5e8f-429">Tabulky a zobrazení</span><span class="sxs-lookup"><span data-stu-id="d5e8f-429">Tables and Views</span></span>  
  
|<span data-ttu-id="d5e8f-430">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="d5e8f-430">ColumnName</span></span>|<span data-ttu-id="d5e8f-431">Datový typ</span><span class="sxs-lookup"><span data-stu-id="d5e8f-431">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d5e8f-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="d5e8f-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="d5e8f-433">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-433">String</span></span>|  
|<span data-ttu-id="d5e8f-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="d5e8f-434">TABLE_OWNER</span></span>|<span data-ttu-id="d5e8f-435">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-435">String</span></span>|  
|<span data-ttu-id="d5e8f-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d5e8f-436">TABLE_NAME</span></span>|<span data-ttu-id="d5e8f-437">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-437">String</span></span>|  
|<span data-ttu-id="d5e8f-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="d5e8f-438">TABLE_TYPE</span></span>|<span data-ttu-id="d5e8f-439">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-439">String</span></span>|  
|<span data-ttu-id="d5e8f-440">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="d5e8f-440">REMARKS</span></span>|<span data-ttu-id="d5e8f-441">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-441">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="d5e8f-442">Sloupce</span><span class="sxs-lookup"><span data-stu-id="d5e8f-442">Columns</span></span>  
  
|<span data-ttu-id="d5e8f-443">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="d5e8f-443">ColumnName</span></span>|<span data-ttu-id="d5e8f-444">Datový typ</span><span class="sxs-lookup"><span data-stu-id="d5e8f-444">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d5e8f-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="d5e8f-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="d5e8f-446">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-446">String</span></span>|  
|<span data-ttu-id="d5e8f-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="d5e8f-447">TABLE_OWNER</span></span>|<span data-ttu-id="d5e8f-448">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-448">String</span></span>|  
|<span data-ttu-id="d5e8f-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d5e8f-449">TABLE_NAME</span></span>|<span data-ttu-id="d5e8f-450">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-450">String</span></span>|  
|<span data-ttu-id="d5e8f-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="d5e8f-451">COLUMN_NAME</span></span>|<span data-ttu-id="d5e8f-452">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-452">String</span></span>|  
|<span data-ttu-id="d5e8f-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="d5e8f-453">DATA_TYPE</span></span>|<span data-ttu-id="d5e8f-454">Int16</span><span class="sxs-lookup"><span data-stu-id="d5e8f-454">Int16</span></span>|  
|<span data-ttu-id="d5e8f-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="d5e8f-455">TYPE_NAME</span></span>|<span data-ttu-id="d5e8f-456">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-456">String</span></span>|  
|<span data-ttu-id="d5e8f-457">PŘESNOST</span><span class="sxs-lookup"><span data-stu-id="d5e8f-457">PRECISION</span></span>|<span data-ttu-id="d5e8f-458">Int32</span><span class="sxs-lookup"><span data-stu-id="d5e8f-458">Int32</span></span>|  
|<span data-ttu-id="d5e8f-459">DÉLKA</span><span class="sxs-lookup"><span data-stu-id="d5e8f-459">LENGTH</span></span>|<span data-ttu-id="d5e8f-460">Int32</span><span class="sxs-lookup"><span data-stu-id="d5e8f-460">Int32</span></span>|  
|<span data-ttu-id="d5e8f-461">ŠKÁLOVÁNÍ</span><span class="sxs-lookup"><span data-stu-id="d5e8f-461">SCALE</span></span>|<span data-ttu-id="d5e8f-462">Int16</span><span class="sxs-lookup"><span data-stu-id="d5e8f-462">Int16</span></span>|  
|<span data-ttu-id="d5e8f-463">RADIX</span><span class="sxs-lookup"><span data-stu-id="d5e8f-463">RADIX</span></span>|<span data-ttu-id="d5e8f-464">Int16</span><span class="sxs-lookup"><span data-stu-id="d5e8f-464">Int16</span></span>|  
|<span data-ttu-id="d5e8f-465">S POVOLENOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="d5e8f-465">NULLABLE</span></span>|<span data-ttu-id="d5e8f-466">Int16</span><span class="sxs-lookup"><span data-stu-id="d5e8f-466">Int16</span></span>|  
|<span data-ttu-id="d5e8f-467">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="d5e8f-467">REMARKS</span></span>|<span data-ttu-id="d5e8f-468">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-468">String</span></span>|  
|<span data-ttu-id="d5e8f-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="d5e8f-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="d5e8f-470">Int32</span><span class="sxs-lookup"><span data-stu-id="d5e8f-470">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="d5e8f-471">Procedury</span><span class="sxs-lookup"><span data-stu-id="d5e8f-471">Procedures</span></span>  
  
|<span data-ttu-id="d5e8f-472">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="d5e8f-472">ColumnName</span></span>|<span data-ttu-id="d5e8f-473">Datový typ</span><span class="sxs-lookup"><span data-stu-id="d5e8f-473">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d5e8f-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="d5e8f-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="d5e8f-475">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-475">String</span></span>|  
|<span data-ttu-id="d5e8f-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="d5e8f-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="d5e8f-477">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-477">String</span></span>|  
|<span data-ttu-id="d5e8f-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="d5e8f-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="d5e8f-479">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-479">String</span></span>|  
|<span data-ttu-id="d5e8f-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="d5e8f-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="d5e8f-481">Int16</span><span class="sxs-lookup"><span data-stu-id="d5e8f-481">Int16</span></span>|  
|<span data-ttu-id="d5e8f-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="d5e8f-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="d5e8f-483">Int16</span><span class="sxs-lookup"><span data-stu-id="d5e8f-483">Int16</span></span>|  
|<span data-ttu-id="d5e8f-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="d5e8f-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="d5e8f-485">Int16</span><span class="sxs-lookup"><span data-stu-id="d5e8f-485">Int16</span></span>|  
|<span data-ttu-id="d5e8f-486">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="d5e8f-486">REMARKS</span></span>|<span data-ttu-id="d5e8f-487">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-487">String</span></span>|  
|<span data-ttu-id="d5e8f-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="d5e8f-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="d5e8f-489">Int16</span><span class="sxs-lookup"><span data-stu-id="d5e8f-489">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="d5e8f-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="d5e8f-490">ProcedureColumns</span></span>  
  
|<span data-ttu-id="d5e8f-491">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="d5e8f-491">ColumnName</span></span>|<span data-ttu-id="d5e8f-492">Datový typ</span><span class="sxs-lookup"><span data-stu-id="d5e8f-492">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d5e8f-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="d5e8f-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="d5e8f-494">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-494">String</span></span>|  
|<span data-ttu-id="d5e8f-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="d5e8f-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="d5e8f-496">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-496">String</span></span>|  
|<span data-ttu-id="d5e8f-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="d5e8f-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="d5e8f-498">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-498">String</span></span>|  
|<span data-ttu-id="d5e8f-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="d5e8f-499">COLUMN_NAME</span></span>|<span data-ttu-id="d5e8f-500">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-500">String</span></span>|  
|<span data-ttu-id="d5e8f-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="d5e8f-501">COLUMN_TYPE</span></span>|<span data-ttu-id="d5e8f-502">Int16</span><span class="sxs-lookup"><span data-stu-id="d5e8f-502">Int16</span></span>|  
|<span data-ttu-id="d5e8f-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="d5e8f-503">DATA_TYPE</span></span>|<span data-ttu-id="d5e8f-504">Int16</span><span class="sxs-lookup"><span data-stu-id="d5e8f-504">Int16</span></span>|  
|<span data-ttu-id="d5e8f-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="d5e8f-505">TYPE_NAME</span></span>|<span data-ttu-id="d5e8f-506">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-506">String</span></span>|  
|<span data-ttu-id="d5e8f-507">PŘESNOST</span><span class="sxs-lookup"><span data-stu-id="d5e8f-507">PRECISION</span></span>|<span data-ttu-id="d5e8f-508">Int32</span><span class="sxs-lookup"><span data-stu-id="d5e8f-508">Int32</span></span>|  
|<span data-ttu-id="d5e8f-509">DÉLKA</span><span class="sxs-lookup"><span data-stu-id="d5e8f-509">LENGTH</span></span>|<span data-ttu-id="d5e8f-510">Int32</span><span class="sxs-lookup"><span data-stu-id="d5e8f-510">Int32</span></span>|  
|<span data-ttu-id="d5e8f-511">ŠKÁLOVÁNÍ</span><span class="sxs-lookup"><span data-stu-id="d5e8f-511">SCALE</span></span>|<span data-ttu-id="d5e8f-512">Int16</span><span class="sxs-lookup"><span data-stu-id="d5e8f-512">Int16</span></span>|  
|<span data-ttu-id="d5e8f-513">RADIX</span><span class="sxs-lookup"><span data-stu-id="d5e8f-513">RADIX</span></span>|<span data-ttu-id="d5e8f-514">Int16</span><span class="sxs-lookup"><span data-stu-id="d5e8f-514">Int16</span></span>|  
|<span data-ttu-id="d5e8f-515">S POVOLENOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="d5e8f-515">NULLABLE</span></span>|<span data-ttu-id="d5e8f-516">Int16</span><span class="sxs-lookup"><span data-stu-id="d5e8f-516">Int16</span></span>|  
|<span data-ttu-id="d5e8f-517">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="d5e8f-517">REMARKS</span></span>|<span data-ttu-id="d5e8f-518">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-518">String</span></span>|  
|<span data-ttu-id="d5e8f-519">PŘETÍŽENÍ</span><span class="sxs-lookup"><span data-stu-id="d5e8f-519">OVERLOAD</span></span>|<span data-ttu-id="d5e8f-520">Int32</span><span class="sxs-lookup"><span data-stu-id="d5e8f-520">Int32</span></span>|  
|<span data-ttu-id="d5e8f-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="d5e8f-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="d5e8f-522">Int32</span><span class="sxs-lookup"><span data-stu-id="d5e8f-522">Int32</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="d5e8f-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="d5e8f-523">ProcedureParameters</span></span>  
  
|<span data-ttu-id="d5e8f-524">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="d5e8f-524">ColumnName</span></span>|<span data-ttu-id="d5e8f-525">Datový typ</span><span class="sxs-lookup"><span data-stu-id="d5e8f-525">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d5e8f-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="d5e8f-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="d5e8f-527">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-527">String</span></span>|  
|<span data-ttu-id="d5e8f-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="d5e8f-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="d5e8f-529">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-529">String</span></span>|  
|<span data-ttu-id="d5e8f-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="d5e8f-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="d5e8f-531">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-531">String</span></span>|  
|<span data-ttu-id="d5e8f-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="d5e8f-532">COLUMN_NAME</span></span>|<span data-ttu-id="d5e8f-533">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-533">String</span></span>|  
|<span data-ttu-id="d5e8f-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="d5e8f-534">COLUMN_TYPE</span></span>|<span data-ttu-id="d5e8f-535">Int16</span><span class="sxs-lookup"><span data-stu-id="d5e8f-535">Int16</span></span>|  
|<span data-ttu-id="d5e8f-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="d5e8f-536">DATA_TYPE</span></span>|<span data-ttu-id="d5e8f-537">Int16</span><span class="sxs-lookup"><span data-stu-id="d5e8f-537">Int16</span></span>|  
|<span data-ttu-id="d5e8f-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="d5e8f-538">TYPE_NAME</span></span>|<span data-ttu-id="d5e8f-539">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-539">String</span></span>|  
|<span data-ttu-id="d5e8f-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="d5e8f-540">COLUMN_SIZE</span></span>|<span data-ttu-id="d5e8f-541">Int32</span><span class="sxs-lookup"><span data-stu-id="d5e8f-541">Int32</span></span>|  
|<span data-ttu-id="d5e8f-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="d5e8f-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="d5e8f-543">Int32</span><span class="sxs-lookup"><span data-stu-id="d5e8f-543">Int32</span></span>|  
|<span data-ttu-id="d5e8f-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="d5e8f-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="d5e8f-545">Int16</span><span class="sxs-lookup"><span data-stu-id="d5e8f-545">Int16</span></span>|  
|<span data-ttu-id="d5e8f-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="d5e8f-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="d5e8f-547">Int16</span><span class="sxs-lookup"><span data-stu-id="d5e8f-547">Int16</span></span>|  
|<span data-ttu-id="d5e8f-548">S POVOLENOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="d5e8f-548">NULLABLE</span></span>|<span data-ttu-id="d5e8f-549">Int16</span><span class="sxs-lookup"><span data-stu-id="d5e8f-549">Int16</span></span>|  
|<span data-ttu-id="d5e8f-550">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="d5e8f-550">REMARKS</span></span>|<span data-ttu-id="d5e8f-551">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-551">String</span></span>|  
|<span data-ttu-id="d5e8f-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="d5e8f-552">COLUMN_DEF</span></span>|<span data-ttu-id="d5e8f-553">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-553">String</span></span>|  
|<span data-ttu-id="d5e8f-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="d5e8f-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="d5e8f-555">Int16</span><span class="sxs-lookup"><span data-stu-id="d5e8f-555">Int16</span></span>|  
|<span data-ttu-id="d5e8f-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="d5e8f-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="d5e8f-557">Int16</span><span class="sxs-lookup"><span data-stu-id="d5e8f-557">Int16</span></span>|  
|<span data-ttu-id="d5e8f-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="d5e8f-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="d5e8f-559">Int32</span><span class="sxs-lookup"><span data-stu-id="d5e8f-559">Int32</span></span>|  
|<span data-ttu-id="d5e8f-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="d5e8f-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="d5e8f-561">Int32</span><span class="sxs-lookup"><span data-stu-id="d5e8f-561">Int32</span></span>|  
|<span data-ttu-id="d5e8f-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="d5e8f-562">IS_NULLABLE</span></span>|<span data-ttu-id="d5e8f-563">String</span><span class="sxs-lookup"><span data-stu-id="d5e8f-563">String</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d5e8f-564">Viz také</span><span class="sxs-lookup"><span data-stu-id="d5e8f-564">See Also</span></span>  
 [<span data-ttu-id="d5e8f-565">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="d5e8f-565">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
