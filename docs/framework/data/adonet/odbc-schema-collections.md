---
title: Kolekce schémat ODBC
ms.date: 03/30/2017
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
ms.openlocfilehash: ffe80120ceffbe29c0a117cf1194860c5782be8c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57365903"
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="1ca95-102">Kolekce schémat ODBC</span><span class="sxs-lookup"><span data-stu-id="1ca95-102">ODBC Schema Collections</span></span>

<span data-ttu-id="1ca95-103">Tato část popisuje kolekci podpora schématu pro ovladače ODBC pro Microsoft SQL Server, Oracle a Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="1ca95-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>

## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="1ca95-104">Ovladač ODBC Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="1ca95-104">Microsoft SQL Server ODBC Driver</span></span>

<span data-ttu-id="1ca95-105">Ovladače ODBC Microsoft SQL Server podporuje následující kolekce určité schéma kromě společné kolekce schémat:</span><span class="sxs-lookup"><span data-stu-id="1ca95-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>

- <span data-ttu-id="1ca95-106">Tabulky</span><span class="sxs-lookup"><span data-stu-id="1ca95-106">Tables</span></span>

- <span data-ttu-id="1ca95-107">Indexy</span><span class="sxs-lookup"><span data-stu-id="1ca95-107">Indexes</span></span>

- <span data-ttu-id="1ca95-108">Sloupce</span><span class="sxs-lookup"><span data-stu-id="1ca95-108">Columns</span></span>

- <span data-ttu-id="1ca95-109">Procedury</span><span class="sxs-lookup"><span data-stu-id="1ca95-109">Procedures</span></span>

- <span data-ttu-id="1ca95-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="1ca95-110">ProcedureColumns</span></span>

- <span data-ttu-id="1ca95-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="1ca95-111">ProcedureParameters</span></span>

- <span data-ttu-id="1ca95-112">Zobrazení</span><span class="sxs-lookup"><span data-stu-id="1ca95-112">Views</span></span>

### <a name="tables-and-views"></a><span data-ttu-id="1ca95-113">Tabulky a zobrazení</span><span class="sxs-lookup"><span data-stu-id="1ca95-113">Tables and Views</span></span>

|<span data-ttu-id="1ca95-114">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="1ca95-114">ColumnName</span></span>|<span data-ttu-id="1ca95-115">DataType</span><span class="sxs-lookup"><span data-stu-id="1ca95-115">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="1ca95-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="1ca95-116">TABLE_CAT</span></span>|<span data-ttu-id="1ca95-117">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-117">String</span></span>|
|<span data-ttu-id="1ca95-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="1ca95-118">TABLE_SCHEM</span></span>|<span data-ttu-id="1ca95-119">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-119">String</span></span>|
|<span data-ttu-id="1ca95-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="1ca95-120">TABLE_NAME</span></span>|<span data-ttu-id="1ca95-121">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-121">String</span></span>|
|<span data-ttu-id="1ca95-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="1ca95-122">TABLE_TYPE</span></span>|<span data-ttu-id="1ca95-123">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-123">String</span></span>|
|<span data-ttu-id="1ca95-124">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="1ca95-124">REMARKS</span></span>|<span data-ttu-id="1ca95-125">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-125">String</span></span>|

### <a name="indexes"></a><span data-ttu-id="1ca95-126">Indexy</span><span class="sxs-lookup"><span data-stu-id="1ca95-126">Indexes</span></span>

|<span data-ttu-id="1ca95-127">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="1ca95-127">ColumnName</span></span>|<span data-ttu-id="1ca95-128">DataType</span><span class="sxs-lookup"><span data-stu-id="1ca95-128">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="1ca95-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="1ca95-129">TABLE_CAT</span></span>|<span data-ttu-id="1ca95-130">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-130">String</span></span>|
|<span data-ttu-id="1ca95-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="1ca95-131">TABLE_SCHEM</span></span>|<span data-ttu-id="1ca95-132">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-132">String</span></span>|
|<span data-ttu-id="1ca95-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="1ca95-133">TABLE_NAME</span></span>|<span data-ttu-id="1ca95-134">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-134">String</span></span>|
|<span data-ttu-id="1ca95-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="1ca95-135">NON_UNIQUE</span></span>|<span data-ttu-id="1ca95-136">Int16</span><span class="sxs-lookup"><span data-stu-id="1ca95-136">Int16</span></span>|
|<span data-ttu-id="1ca95-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="1ca95-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="1ca95-138">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-138">String</span></span>|
|<span data-ttu-id="1ca95-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="1ca95-139">INDEX_NAME</span></span>|<span data-ttu-id="1ca95-140">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-140">String</span></span>|
|<span data-ttu-id="1ca95-141">TYP</span><span class="sxs-lookup"><span data-stu-id="1ca95-141">TYPE</span></span>|<span data-ttu-id="1ca95-142">Int16</span><span class="sxs-lookup"><span data-stu-id="1ca95-142">Int16</span></span>|
|<span data-ttu-id="1ca95-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="1ca95-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="1ca95-144">Int16</span><span class="sxs-lookup"><span data-stu-id="1ca95-144">Int16</span></span>|
|<span data-ttu-id="1ca95-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="1ca95-145">COLUMN_NAME</span></span>|<span data-ttu-id="1ca95-146">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-146">String</span></span>|
|<span data-ttu-id="1ca95-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="1ca95-147">ASC_OR_DESC</span></span>|<span data-ttu-id="1ca95-148">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-148">String</span></span>|
|<span data-ttu-id="1ca95-149">KARDINALITA</span><span class="sxs-lookup"><span data-stu-id="1ca95-149">CARDINALITY</span></span>|<span data-ttu-id="1ca95-150">Int32</span><span class="sxs-lookup"><span data-stu-id="1ca95-150">Int32</span></span>|
|<span data-ttu-id="1ca95-151">STRÁNKY</span><span class="sxs-lookup"><span data-stu-id="1ca95-151">PAGES</span></span>|<span data-ttu-id="1ca95-152">Int32</span><span class="sxs-lookup"><span data-stu-id="1ca95-152">Int32</span></span>|
|<span data-ttu-id="1ca95-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="1ca95-153">FILTER_CONDITION</span></span>|<span data-ttu-id="1ca95-154">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-154">String</span></span>|
|<span data-ttu-id="1ca95-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="1ca95-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="1ca95-156">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-156">String</span></span>|
|<span data-ttu-id="1ca95-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="1ca95-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="1ca95-158">Byte</span><span class="sxs-lookup"><span data-stu-id="1ca95-158">Byte</span></span>|

### <a name="columns"></a><span data-ttu-id="1ca95-159">Sloupce</span><span class="sxs-lookup"><span data-stu-id="1ca95-159">Columns</span></span>

|<span data-ttu-id="1ca95-160">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="1ca95-160">ColumnName</span></span>|<span data-ttu-id="1ca95-161">DataType</span><span class="sxs-lookup"><span data-stu-id="1ca95-161">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="1ca95-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="1ca95-162">TABLE_CAT</span></span>|<span data-ttu-id="1ca95-163">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-163">String</span></span>|
|<span data-ttu-id="1ca95-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="1ca95-164">TABLE_SCHEM</span></span>|<span data-ttu-id="1ca95-165">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-165">String</span></span>|
|<span data-ttu-id="1ca95-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="1ca95-166">TABLE_NAME</span></span>|<span data-ttu-id="1ca95-167">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-167">String</span></span>|
|<span data-ttu-id="1ca95-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="1ca95-168">COLUMN_NAME</span></span>|<span data-ttu-id="1ca95-169">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-169">String</span></span>|
|<span data-ttu-id="1ca95-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="1ca95-170">DATA_TYPE</span></span>|<span data-ttu-id="1ca95-171">Int16</span><span class="sxs-lookup"><span data-stu-id="1ca95-171">Int16</span></span>|
|<span data-ttu-id="1ca95-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="1ca95-172">TYPE_NAME</span></span>|<span data-ttu-id="1ca95-173">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-173">String</span></span>|
|<span data-ttu-id="1ca95-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="1ca95-174">COLUMN_SIZE</span></span>|<span data-ttu-id="1ca95-175">Int32</span><span class="sxs-lookup"><span data-stu-id="1ca95-175">Int32</span></span>|
|<span data-ttu-id="1ca95-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="1ca95-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="1ca95-177">Int32</span><span class="sxs-lookup"><span data-stu-id="1ca95-177">Int32</span></span>|
|<span data-ttu-id="1ca95-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="1ca95-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="1ca95-179">Int16</span><span class="sxs-lookup"><span data-stu-id="1ca95-179">Int16</span></span>|
|<span data-ttu-id="1ca95-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="1ca95-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="1ca95-181">Int16</span><span class="sxs-lookup"><span data-stu-id="1ca95-181">Int16</span></span>|
|<span data-ttu-id="1ca95-182">S POVOLENOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="1ca95-182">NULLABLE</span></span>|<span data-ttu-id="1ca95-183">Int16</span><span class="sxs-lookup"><span data-stu-id="1ca95-183">Int16</span></span>|
|<span data-ttu-id="1ca95-184">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="1ca95-184">REMARKS</span></span>|<span data-ttu-id="1ca95-185">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-185">String</span></span>|
|<span data-ttu-id="1ca95-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="1ca95-186">COLUMN_DEF</span></span>|<span data-ttu-id="1ca95-187">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-187">String</span></span>|
|<span data-ttu-id="1ca95-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="1ca95-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="1ca95-189">Int16</span><span class="sxs-lookup"><span data-stu-id="1ca95-189">Int16</span></span>|
|<span data-ttu-id="1ca95-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="1ca95-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="1ca95-191">Int16</span><span class="sxs-lookup"><span data-stu-id="1ca95-191">Int16</span></span>|
|<span data-ttu-id="1ca95-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="1ca95-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="1ca95-193">Int32</span><span class="sxs-lookup"><span data-stu-id="1ca95-193">Int32</span></span>|
|<span data-ttu-id="1ca95-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="1ca95-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="1ca95-195">Int32</span><span class="sxs-lookup"><span data-stu-id="1ca95-195">Int32</span></span>|
|<span data-ttu-id="1ca95-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="1ca95-196">IS_NULLABLE</span></span>|<span data-ttu-id="1ca95-197">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-197">String</span></span>|
|<span data-ttu-id="1ca95-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="1ca95-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="1ca95-199">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-199">String</span></span>|
|<span data-ttu-id="1ca95-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="1ca95-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="1ca95-201">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-201">String</span></span>|
|<span data-ttu-id="1ca95-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="1ca95-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="1ca95-203">Byte</span><span class="sxs-lookup"><span data-stu-id="1ca95-203">Byte</span></span>|

### <a name="procedures"></a><span data-ttu-id="1ca95-204">Procedury</span><span class="sxs-lookup"><span data-stu-id="1ca95-204">Procedures</span></span>

|<span data-ttu-id="1ca95-205">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="1ca95-205">ColumnName</span></span>|<span data-ttu-id="1ca95-206">DataType</span><span class="sxs-lookup"><span data-stu-id="1ca95-206">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="1ca95-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="1ca95-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="1ca95-208">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-208">String</span></span>|
|<span data-ttu-id="1ca95-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="1ca95-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="1ca95-210">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-210">String</span></span>|
|<span data-ttu-id="1ca95-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="1ca95-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="1ca95-212">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-212">String</span></span>|
|<span data-ttu-id="1ca95-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="1ca95-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="1ca95-214">Int32</span><span class="sxs-lookup"><span data-stu-id="1ca95-214">Int32</span></span>|
|<span data-ttu-id="1ca95-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="1ca95-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="1ca95-216">Int32</span><span class="sxs-lookup"><span data-stu-id="1ca95-216">Int32</span></span>|
|<span data-ttu-id="1ca95-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="1ca95-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="1ca95-218">Int32</span><span class="sxs-lookup"><span data-stu-id="1ca95-218">Int32</span></span>|
|<span data-ttu-id="1ca95-219">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="1ca95-219">REMARKS</span></span>|<span data-ttu-id="1ca95-220">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-220">String</span></span>|
|<span data-ttu-id="1ca95-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="1ca95-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="1ca95-222">Int16</span><span class="sxs-lookup"><span data-stu-id="1ca95-222">Int16</span></span>|

### <a name="procedurecolumns"></a><span data-ttu-id="1ca95-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="1ca95-223">ProcedureColumns</span></span>

|<span data-ttu-id="1ca95-224">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="1ca95-224">ColumnName</span></span>|<span data-ttu-id="1ca95-225">DataType</span><span class="sxs-lookup"><span data-stu-id="1ca95-225">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="1ca95-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="1ca95-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="1ca95-227">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-227">String</span></span>|
|<span data-ttu-id="1ca95-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="1ca95-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="1ca95-229">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-229">String</span></span>|
|<span data-ttu-id="1ca95-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="1ca95-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="1ca95-231">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-231">String</span></span>|
|<span data-ttu-id="1ca95-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="1ca95-232">COLUMN_NAME</span></span>|<span data-ttu-id="1ca95-233">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-233">String</span></span>|
|<span data-ttu-id="1ca95-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="1ca95-234">COLUMN_TYPE</span></span>|<span data-ttu-id="1ca95-235">Int16</span><span class="sxs-lookup"><span data-stu-id="1ca95-235">Int16</span></span>|
|<span data-ttu-id="1ca95-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="1ca95-236">DATA_TYPE</span></span>|<span data-ttu-id="1ca95-237">Int16</span><span class="sxs-lookup"><span data-stu-id="1ca95-237">Int16</span></span>|
|<span data-ttu-id="1ca95-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="1ca95-238">TYPE_NAME</span></span>|<span data-ttu-id="1ca95-239">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-239">String</span></span>|
|<span data-ttu-id="1ca95-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="1ca95-240">COLUMN_SIZE</span></span>|<span data-ttu-id="1ca95-241">Int32</span><span class="sxs-lookup"><span data-stu-id="1ca95-241">Int32</span></span>|
|<span data-ttu-id="1ca95-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="1ca95-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="1ca95-243">Int32</span><span class="sxs-lookup"><span data-stu-id="1ca95-243">Int32</span></span>|
|<span data-ttu-id="1ca95-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="1ca95-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="1ca95-245">Int16</span><span class="sxs-lookup"><span data-stu-id="1ca95-245">Int16</span></span>|
|<span data-ttu-id="1ca95-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="1ca95-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="1ca95-247">Int16</span><span class="sxs-lookup"><span data-stu-id="1ca95-247">Int16</span></span>|
|<span data-ttu-id="1ca95-248">S POVOLENOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="1ca95-248">NULLABLE</span></span>|<span data-ttu-id="1ca95-249">Int16</span><span class="sxs-lookup"><span data-stu-id="1ca95-249">Int16</span></span>|
|<span data-ttu-id="1ca95-250">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="1ca95-250">REMARKS</span></span>|<span data-ttu-id="1ca95-251">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-251">String</span></span>|
|<span data-ttu-id="1ca95-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="1ca95-252">COLUMN_DEF</span></span>|<span data-ttu-id="1ca95-253">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-253">String</span></span>|
|<span data-ttu-id="1ca95-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="1ca95-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="1ca95-255">Int16</span><span class="sxs-lookup"><span data-stu-id="1ca95-255">Int16</span></span>|
|<span data-ttu-id="1ca95-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="1ca95-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="1ca95-257">Int16</span><span class="sxs-lookup"><span data-stu-id="1ca95-257">Int16</span></span>|
|<span data-ttu-id="1ca95-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="1ca95-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="1ca95-259">Int32</span><span class="sxs-lookup"><span data-stu-id="1ca95-259">Int32</span></span>|
|<span data-ttu-id="1ca95-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="1ca95-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="1ca95-261">Int32</span><span class="sxs-lookup"><span data-stu-id="1ca95-261">Int32</span></span>|
|<span data-ttu-id="1ca95-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="1ca95-262">IS_NULLABLE</span></span>|<span data-ttu-id="1ca95-263">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-263">String</span></span>|
|<span data-ttu-id="1ca95-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="1ca95-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="1ca95-265">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-265">String</span></span>|
|<span data-ttu-id="1ca95-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="1ca95-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="1ca95-267">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-267">String</span></span>|
|<span data-ttu-id="1ca95-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="1ca95-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="1ca95-269">Byte</span><span class="sxs-lookup"><span data-stu-id="1ca95-269">Byte</span></span>|

### <a name="procedureparameters"></a><span data-ttu-id="1ca95-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="1ca95-270">ProcedureParameters</span></span>

|<span data-ttu-id="1ca95-271">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="1ca95-271">ColumnName</span></span>|<span data-ttu-id="1ca95-272">DataType</span><span class="sxs-lookup"><span data-stu-id="1ca95-272">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="1ca95-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="1ca95-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="1ca95-274">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-274">String</span></span>|
|<span data-ttu-id="1ca95-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="1ca95-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="1ca95-276">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-276">String</span></span>|
|<span data-ttu-id="1ca95-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="1ca95-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="1ca95-278">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-278">String</span></span>|
|<span data-ttu-id="1ca95-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="1ca95-279">COLUMN_NAME</span></span>|<span data-ttu-id="1ca95-280">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-280">String</span></span>|
|<span data-ttu-id="1ca95-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="1ca95-281">COLUMN_TYPE</span></span>|<span data-ttu-id="1ca95-282">Int16</span><span class="sxs-lookup"><span data-stu-id="1ca95-282">Int16</span></span>|
|<span data-ttu-id="1ca95-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="1ca95-283">DATA_TYPE</span></span>|<span data-ttu-id="1ca95-284">Int16</span><span class="sxs-lookup"><span data-stu-id="1ca95-284">Int16</span></span>|
|<span data-ttu-id="1ca95-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="1ca95-285">TYPE_NAME</span></span>|<span data-ttu-id="1ca95-286">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-286">String</span></span>|
|<span data-ttu-id="1ca95-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="1ca95-287">COLUMN_SIZE</span></span>|<span data-ttu-id="1ca95-288">Int32</span><span class="sxs-lookup"><span data-stu-id="1ca95-288">Int32</span></span>|
|<span data-ttu-id="1ca95-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="1ca95-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="1ca95-290">Int32</span><span class="sxs-lookup"><span data-stu-id="1ca95-290">Int32</span></span>|
|<span data-ttu-id="1ca95-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="1ca95-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="1ca95-292">Int16</span><span class="sxs-lookup"><span data-stu-id="1ca95-292">Int16</span></span>|
|<span data-ttu-id="1ca95-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="1ca95-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="1ca95-294">Int16</span><span class="sxs-lookup"><span data-stu-id="1ca95-294">Int16</span></span>|
|<span data-ttu-id="1ca95-295">S POVOLENOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="1ca95-295">NULLABLE</span></span>|<span data-ttu-id="1ca95-296">Int16</span><span class="sxs-lookup"><span data-stu-id="1ca95-296">Int16</span></span>|
|<span data-ttu-id="1ca95-297">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="1ca95-297">REMARKS</span></span>|<span data-ttu-id="1ca95-298">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-298">String</span></span>|
|<span data-ttu-id="1ca95-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="1ca95-299">COLUMN_DEF</span></span>|<span data-ttu-id="1ca95-300">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-300">String</span></span>|
|<span data-ttu-id="1ca95-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="1ca95-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="1ca95-302">Int16</span><span class="sxs-lookup"><span data-stu-id="1ca95-302">Int16</span></span>|
|<span data-ttu-id="1ca95-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="1ca95-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="1ca95-304">Int16</span><span class="sxs-lookup"><span data-stu-id="1ca95-304">Int16</span></span>|
|<span data-ttu-id="1ca95-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="1ca95-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="1ca95-306">Int32</span><span class="sxs-lookup"><span data-stu-id="1ca95-306">Int32</span></span>|
|<span data-ttu-id="1ca95-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="1ca95-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="1ca95-308">Int32</span><span class="sxs-lookup"><span data-stu-id="1ca95-308">Int32</span></span>|
|<span data-ttu-id="1ca95-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="1ca95-309">IS_NULLABLE</span></span>|<span data-ttu-id="1ca95-310">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-310">String</span></span>|
|<span data-ttu-id="1ca95-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="1ca95-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="1ca95-312">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-312">String</span></span>|
|<span data-ttu-id="1ca95-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="1ca95-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="1ca95-314">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-314">String</span></span>|
|<span data-ttu-id="1ca95-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="1ca95-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="1ca95-316">Byte</span><span class="sxs-lookup"><span data-stu-id="1ca95-316">Byte</span></span>|

## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="1ca95-317">Ovladač ODBC Microsoft Oracle</span><span class="sxs-lookup"><span data-stu-id="1ca95-317">Microsoft Oracle ODBC Driver</span></span>

<span data-ttu-id="1ca95-318">Ovladače ODBC Microsoft SQL Server Oracle podporuje následující kolekce určité schéma kromě společné kolekce schémat:</span><span class="sxs-lookup"><span data-stu-id="1ca95-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>

- <span data-ttu-id="1ca95-319">Tabulky</span><span class="sxs-lookup"><span data-stu-id="1ca95-319">Tables</span></span>

- <span data-ttu-id="1ca95-320">Sloupce</span><span class="sxs-lookup"><span data-stu-id="1ca95-320">Columns</span></span>

- <span data-ttu-id="1ca95-321">Procedury</span><span class="sxs-lookup"><span data-stu-id="1ca95-321">Procedures</span></span>

- <span data-ttu-id="1ca95-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="1ca95-322">ProcedureColumns</span></span>

- <span data-ttu-id="1ca95-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="1ca95-323">ProcedureParameters</span></span>

- <span data-ttu-id="1ca95-324">Zobrazení</span><span class="sxs-lookup"><span data-stu-id="1ca95-324">Views</span></span>

- <span data-ttu-id="1ca95-325">Indexy</span><span class="sxs-lookup"><span data-stu-id="1ca95-325">Indexes</span></span>

### <a name="tables-and-views"></a><span data-ttu-id="1ca95-326">Tabulky a zobrazení</span><span class="sxs-lookup"><span data-stu-id="1ca95-326">Tables and Views</span></span>

|<span data-ttu-id="1ca95-327">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="1ca95-327">ColumnName</span></span>|<span data-ttu-id="1ca95-328">DataType</span><span class="sxs-lookup"><span data-stu-id="1ca95-328">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="1ca95-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="1ca95-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="1ca95-330">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-330">String</span></span>|
|<span data-ttu-id="1ca95-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="1ca95-331">TABLE_OWNER</span></span>|<span data-ttu-id="1ca95-332">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-332">String</span></span>|
|<span data-ttu-id="1ca95-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="1ca95-333">TABLE_NAME</span></span>|<span data-ttu-id="1ca95-334">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-334">String</span></span>|
|<span data-ttu-id="1ca95-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="1ca95-335">TABLE_TYPE</span></span>|<span data-ttu-id="1ca95-336">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-336">String</span></span>|
|<span data-ttu-id="1ca95-337">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="1ca95-337">REMARKS</span></span>|<span data-ttu-id="1ca95-338">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-338">String</span></span>|

### <a name="columns"></a><span data-ttu-id="1ca95-339">Sloupce</span><span class="sxs-lookup"><span data-stu-id="1ca95-339">Columns</span></span>

|<span data-ttu-id="1ca95-340">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="1ca95-340">ColumnName</span></span>|<span data-ttu-id="1ca95-341">DataType</span><span class="sxs-lookup"><span data-stu-id="1ca95-341">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="1ca95-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="1ca95-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="1ca95-343">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-343">String</span></span>|
|<span data-ttu-id="1ca95-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="1ca95-344">TABLE_OWNER</span></span>|<span data-ttu-id="1ca95-345">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-345">String</span></span>|
|<span data-ttu-id="1ca95-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="1ca95-346">TABLE_NAME</span></span>|<span data-ttu-id="1ca95-347">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-347">String</span></span>|
|<span data-ttu-id="1ca95-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="1ca95-348">COLUMN_NAME</span></span>|<span data-ttu-id="1ca95-349">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-349">String</span></span>|
|<span data-ttu-id="1ca95-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="1ca95-350">DATA_TYPE</span></span>|<span data-ttu-id="1ca95-351">Int16</span><span class="sxs-lookup"><span data-stu-id="1ca95-351">Int16</span></span>|
|<span data-ttu-id="1ca95-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="1ca95-352">TYPE_NAME</span></span>|<span data-ttu-id="1ca95-353">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-353">String</span></span>|
|<span data-ttu-id="1ca95-354">PŘESNOST</span><span class="sxs-lookup"><span data-stu-id="1ca95-354">PRECISION</span></span>|<span data-ttu-id="1ca95-355">Int32</span><span class="sxs-lookup"><span data-stu-id="1ca95-355">Int32</span></span>|
|<span data-ttu-id="1ca95-356">DÉLKA</span><span class="sxs-lookup"><span data-stu-id="1ca95-356">LENGTH</span></span>|<span data-ttu-id="1ca95-357">Int32</span><span class="sxs-lookup"><span data-stu-id="1ca95-357">Int32</span></span>|
|<span data-ttu-id="1ca95-358">ŠKÁLOVÁNÍ</span><span class="sxs-lookup"><span data-stu-id="1ca95-358">SCALE</span></span>|<span data-ttu-id="1ca95-359">Int16</span><span class="sxs-lookup"><span data-stu-id="1ca95-359">Int16</span></span>|
|<span data-ttu-id="1ca95-360">RADIX</span><span class="sxs-lookup"><span data-stu-id="1ca95-360">RADIX</span></span>|<span data-ttu-id="1ca95-361">Int16</span><span class="sxs-lookup"><span data-stu-id="1ca95-361">Int16</span></span>|
|<span data-ttu-id="1ca95-362">S POVOLENOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="1ca95-362">NULLABLE</span></span>|<span data-ttu-id="1ca95-363">Int16</span><span class="sxs-lookup"><span data-stu-id="1ca95-363">Int16</span></span>|
|<span data-ttu-id="1ca95-364">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="1ca95-364">REMARKS</span></span>|<span data-ttu-id="1ca95-365">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-365">String</span></span>|
|<span data-ttu-id="1ca95-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="1ca95-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="1ca95-367">Int32</span><span class="sxs-lookup"><span data-stu-id="1ca95-367">Int32</span></span>|

### <a name="procedures"></a><span data-ttu-id="1ca95-368">Procedury</span><span class="sxs-lookup"><span data-stu-id="1ca95-368">Procedures</span></span>

|<span data-ttu-id="1ca95-369">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="1ca95-369">ColumnName</span></span>|<span data-ttu-id="1ca95-370">DataType</span><span class="sxs-lookup"><span data-stu-id="1ca95-370">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="1ca95-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="1ca95-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="1ca95-372">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-372">String</span></span>|
|<span data-ttu-id="1ca95-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="1ca95-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="1ca95-374">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-374">String</span></span>|
|<span data-ttu-id="1ca95-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="1ca95-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="1ca95-376">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-376">String</span></span>|
|<span data-ttu-id="1ca95-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="1ca95-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="1ca95-378">Int16</span><span class="sxs-lookup"><span data-stu-id="1ca95-378">Int16</span></span>|
|<span data-ttu-id="1ca95-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="1ca95-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="1ca95-380">Int16</span><span class="sxs-lookup"><span data-stu-id="1ca95-380">Int16</span></span>|
|<span data-ttu-id="1ca95-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="1ca95-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="1ca95-382">Int16</span><span class="sxs-lookup"><span data-stu-id="1ca95-382">Int16</span></span>|
|<span data-ttu-id="1ca95-383">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="1ca95-383">REMARKS</span></span>|<span data-ttu-id="1ca95-384">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-384">String</span></span>|
|<span data-ttu-id="1ca95-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="1ca95-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="1ca95-386">Int16</span><span class="sxs-lookup"><span data-stu-id="1ca95-386">Int16</span></span>|

### <a name="procedurecolumns"></a><span data-ttu-id="1ca95-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="1ca95-387">ProcedureColumns</span></span>

|<span data-ttu-id="1ca95-388">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="1ca95-388">ColumnName</span></span>|<span data-ttu-id="1ca95-389">DataType</span><span class="sxs-lookup"><span data-stu-id="1ca95-389">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="1ca95-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="1ca95-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="1ca95-391">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-391">String</span></span>|
|<span data-ttu-id="1ca95-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="1ca95-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="1ca95-393">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-393">String</span></span>|
|<span data-ttu-id="1ca95-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="1ca95-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="1ca95-395">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-395">String</span></span>|
|<span data-ttu-id="1ca95-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="1ca95-396">COLUMN_NAME</span></span>|<span data-ttu-id="1ca95-397">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-397">String</span></span>|
|<span data-ttu-id="1ca95-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="1ca95-398">COLUMN_TYPE</span></span>|<span data-ttu-id="1ca95-399">Int16</span><span class="sxs-lookup"><span data-stu-id="1ca95-399">Int16</span></span>|
|<span data-ttu-id="1ca95-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="1ca95-400">DATA_TYPE</span></span>|<span data-ttu-id="1ca95-401">Int16</span><span class="sxs-lookup"><span data-stu-id="1ca95-401">Int16</span></span>|
|<span data-ttu-id="1ca95-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="1ca95-402">TYPE_NAME</span></span>|<span data-ttu-id="1ca95-403">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-403">String</span></span>|
|<span data-ttu-id="1ca95-404">PŘESNOST</span><span class="sxs-lookup"><span data-stu-id="1ca95-404">PRECISION</span></span>|<span data-ttu-id="1ca95-405">Int32</span><span class="sxs-lookup"><span data-stu-id="1ca95-405">Int32</span></span>|
|<span data-ttu-id="1ca95-406">DÉLKA</span><span class="sxs-lookup"><span data-stu-id="1ca95-406">LENGTH</span></span>|<span data-ttu-id="1ca95-407">Int32</span><span class="sxs-lookup"><span data-stu-id="1ca95-407">Int32</span></span>|
|<span data-ttu-id="1ca95-408">ŠKÁLOVÁNÍ</span><span class="sxs-lookup"><span data-stu-id="1ca95-408">SCALE</span></span>|<span data-ttu-id="1ca95-409">Int16</span><span class="sxs-lookup"><span data-stu-id="1ca95-409">Int16</span></span>|
|<span data-ttu-id="1ca95-410">RADIX</span><span class="sxs-lookup"><span data-stu-id="1ca95-410">RADIX</span></span>|<span data-ttu-id="1ca95-411">Int16</span><span class="sxs-lookup"><span data-stu-id="1ca95-411">Int16</span></span>|
|<span data-ttu-id="1ca95-412">S POVOLENOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="1ca95-412">NULLABLE</span></span>|<span data-ttu-id="1ca95-413">Int16</span><span class="sxs-lookup"><span data-stu-id="1ca95-413">Int16</span></span>|
|<span data-ttu-id="1ca95-414">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="1ca95-414">REMARKS</span></span>|<span data-ttu-id="1ca95-415">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-415">String</span></span>|
|<span data-ttu-id="1ca95-416">PŘETÍŽENÍ</span><span class="sxs-lookup"><span data-stu-id="1ca95-416">OVERLOAD</span></span>|<span data-ttu-id="1ca95-417">Int32</span><span class="sxs-lookup"><span data-stu-id="1ca95-417">Int32</span></span>|
|<span data-ttu-id="1ca95-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="1ca95-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="1ca95-419">Int32</span><span class="sxs-lookup"><span data-stu-id="1ca95-419">Int32</span></span>|

## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="1ca95-420">Ovladač ODBC Microsoft Jet</span><span class="sxs-lookup"><span data-stu-id="1ca95-420">Microsoft Jet ODBC Driver</span></span>

<span data-ttu-id="1ca95-421">Ovladač ODBC Microsoft Jet podporuje následující kolekce určité schéma kromě společné kolekce schémat:</span><span class="sxs-lookup"><span data-stu-id="1ca95-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>

- <span data-ttu-id="1ca95-422">Tabulky</span><span class="sxs-lookup"><span data-stu-id="1ca95-422">Tables</span></span>

- <span data-ttu-id="1ca95-423">Indexy</span><span class="sxs-lookup"><span data-stu-id="1ca95-423">Indexes</span></span>

- <span data-ttu-id="1ca95-424">Sloupce</span><span class="sxs-lookup"><span data-stu-id="1ca95-424">Columns</span></span>

- <span data-ttu-id="1ca95-425">Procedury</span><span class="sxs-lookup"><span data-stu-id="1ca95-425">Procedures</span></span>

- <span data-ttu-id="1ca95-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="1ca95-426">ProcedureColumns</span></span>

- <span data-ttu-id="1ca95-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="1ca95-427">ProcedureParameters</span></span>

- <span data-ttu-id="1ca95-428">Zobrazení</span><span class="sxs-lookup"><span data-stu-id="1ca95-428">Views</span></span>

### <a name="tables-and-views"></a><span data-ttu-id="1ca95-429">Tabulky a zobrazení</span><span class="sxs-lookup"><span data-stu-id="1ca95-429">Tables and Views</span></span>

|<span data-ttu-id="1ca95-430">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="1ca95-430">ColumnName</span></span>|<span data-ttu-id="1ca95-431">DataType</span><span class="sxs-lookup"><span data-stu-id="1ca95-431">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="1ca95-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="1ca95-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="1ca95-433">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-433">String</span></span>|
|<span data-ttu-id="1ca95-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="1ca95-434">TABLE_OWNER</span></span>|<span data-ttu-id="1ca95-435">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-435">String</span></span>|
|<span data-ttu-id="1ca95-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="1ca95-436">TABLE_NAME</span></span>|<span data-ttu-id="1ca95-437">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-437">String</span></span>|
|<span data-ttu-id="1ca95-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="1ca95-438">TABLE_TYPE</span></span>|<span data-ttu-id="1ca95-439">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-439">String</span></span>|
|<span data-ttu-id="1ca95-440">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="1ca95-440">REMARKS</span></span>|<span data-ttu-id="1ca95-441">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-441">String</span></span>|

### <a name="columns"></a><span data-ttu-id="1ca95-442">Sloupce</span><span class="sxs-lookup"><span data-stu-id="1ca95-442">Columns</span></span>

|<span data-ttu-id="1ca95-443">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="1ca95-443">ColumnName</span></span>|<span data-ttu-id="1ca95-444">DataType</span><span class="sxs-lookup"><span data-stu-id="1ca95-444">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="1ca95-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="1ca95-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="1ca95-446">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-446">String</span></span>|
|<span data-ttu-id="1ca95-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="1ca95-447">TABLE_OWNER</span></span>|<span data-ttu-id="1ca95-448">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-448">String</span></span>|
|<span data-ttu-id="1ca95-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="1ca95-449">TABLE_NAME</span></span>|<span data-ttu-id="1ca95-450">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-450">String</span></span>|
|<span data-ttu-id="1ca95-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="1ca95-451">COLUMN_NAME</span></span>|<span data-ttu-id="1ca95-452">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-452">String</span></span>|
|<span data-ttu-id="1ca95-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="1ca95-453">DATA_TYPE</span></span>|<span data-ttu-id="1ca95-454">Int16</span><span class="sxs-lookup"><span data-stu-id="1ca95-454">Int16</span></span>|
|<span data-ttu-id="1ca95-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="1ca95-455">TYPE_NAME</span></span>|<span data-ttu-id="1ca95-456">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-456">String</span></span>|
|<span data-ttu-id="1ca95-457">PŘESNOST</span><span class="sxs-lookup"><span data-stu-id="1ca95-457">PRECISION</span></span>|<span data-ttu-id="1ca95-458">Int32</span><span class="sxs-lookup"><span data-stu-id="1ca95-458">Int32</span></span>|
|<span data-ttu-id="1ca95-459">DÉLKA</span><span class="sxs-lookup"><span data-stu-id="1ca95-459">LENGTH</span></span>|<span data-ttu-id="1ca95-460">Int32</span><span class="sxs-lookup"><span data-stu-id="1ca95-460">Int32</span></span>|
|<span data-ttu-id="1ca95-461">ŠKÁLOVÁNÍ</span><span class="sxs-lookup"><span data-stu-id="1ca95-461">SCALE</span></span>|<span data-ttu-id="1ca95-462">Int16</span><span class="sxs-lookup"><span data-stu-id="1ca95-462">Int16</span></span>|
|<span data-ttu-id="1ca95-463">RADIX</span><span class="sxs-lookup"><span data-stu-id="1ca95-463">RADIX</span></span>|<span data-ttu-id="1ca95-464">Int16</span><span class="sxs-lookup"><span data-stu-id="1ca95-464">Int16</span></span>|
|<span data-ttu-id="1ca95-465">S POVOLENOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="1ca95-465">NULLABLE</span></span>|<span data-ttu-id="1ca95-466">Int16</span><span class="sxs-lookup"><span data-stu-id="1ca95-466">Int16</span></span>|
|<span data-ttu-id="1ca95-467">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="1ca95-467">REMARKS</span></span>|<span data-ttu-id="1ca95-468">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-468">String</span></span>|
|<span data-ttu-id="1ca95-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="1ca95-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="1ca95-470">Int32</span><span class="sxs-lookup"><span data-stu-id="1ca95-470">Int32</span></span>|

### <a name="procedures"></a><span data-ttu-id="1ca95-471">Procedury</span><span class="sxs-lookup"><span data-stu-id="1ca95-471">Procedures</span></span>

|<span data-ttu-id="1ca95-472">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="1ca95-472">ColumnName</span></span>|<span data-ttu-id="1ca95-473">DataType</span><span class="sxs-lookup"><span data-stu-id="1ca95-473">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="1ca95-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="1ca95-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="1ca95-475">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-475">String</span></span>|
|<span data-ttu-id="1ca95-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="1ca95-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="1ca95-477">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-477">String</span></span>|
|<span data-ttu-id="1ca95-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="1ca95-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="1ca95-479">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-479">String</span></span>|
|<span data-ttu-id="1ca95-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="1ca95-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="1ca95-481">Int16</span><span class="sxs-lookup"><span data-stu-id="1ca95-481">Int16</span></span>|
|<span data-ttu-id="1ca95-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="1ca95-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="1ca95-483">Int16</span><span class="sxs-lookup"><span data-stu-id="1ca95-483">Int16</span></span>|
|<span data-ttu-id="1ca95-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="1ca95-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="1ca95-485">Int16</span><span class="sxs-lookup"><span data-stu-id="1ca95-485">Int16</span></span>|
|<span data-ttu-id="1ca95-486">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="1ca95-486">REMARKS</span></span>|<span data-ttu-id="1ca95-487">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-487">String</span></span>|
|<span data-ttu-id="1ca95-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="1ca95-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="1ca95-489">Int16</span><span class="sxs-lookup"><span data-stu-id="1ca95-489">Int16</span></span>|

### <a name="procedurecolumns"></a><span data-ttu-id="1ca95-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="1ca95-490">ProcedureColumns</span></span>

|<span data-ttu-id="1ca95-491">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="1ca95-491">ColumnName</span></span>|<span data-ttu-id="1ca95-492">DataType</span><span class="sxs-lookup"><span data-stu-id="1ca95-492">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="1ca95-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="1ca95-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="1ca95-494">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-494">String</span></span>|
|<span data-ttu-id="1ca95-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="1ca95-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="1ca95-496">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-496">String</span></span>|
|<span data-ttu-id="1ca95-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="1ca95-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="1ca95-498">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-498">String</span></span>|
|<span data-ttu-id="1ca95-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="1ca95-499">COLUMN_NAME</span></span>|<span data-ttu-id="1ca95-500">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-500">String</span></span>|
|<span data-ttu-id="1ca95-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="1ca95-501">COLUMN_TYPE</span></span>|<span data-ttu-id="1ca95-502">Int16</span><span class="sxs-lookup"><span data-stu-id="1ca95-502">Int16</span></span>|
|<span data-ttu-id="1ca95-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="1ca95-503">DATA_TYPE</span></span>|<span data-ttu-id="1ca95-504">Int16</span><span class="sxs-lookup"><span data-stu-id="1ca95-504">Int16</span></span>|
|<span data-ttu-id="1ca95-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="1ca95-505">TYPE_NAME</span></span>|<span data-ttu-id="1ca95-506">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-506">String</span></span>|
|<span data-ttu-id="1ca95-507">PŘESNOST</span><span class="sxs-lookup"><span data-stu-id="1ca95-507">PRECISION</span></span>|<span data-ttu-id="1ca95-508">Int32</span><span class="sxs-lookup"><span data-stu-id="1ca95-508">Int32</span></span>|
|<span data-ttu-id="1ca95-509">DÉLKA</span><span class="sxs-lookup"><span data-stu-id="1ca95-509">LENGTH</span></span>|<span data-ttu-id="1ca95-510">Int32</span><span class="sxs-lookup"><span data-stu-id="1ca95-510">Int32</span></span>|
|<span data-ttu-id="1ca95-511">ŠKÁLOVÁNÍ</span><span class="sxs-lookup"><span data-stu-id="1ca95-511">SCALE</span></span>|<span data-ttu-id="1ca95-512">Int16</span><span class="sxs-lookup"><span data-stu-id="1ca95-512">Int16</span></span>|
|<span data-ttu-id="1ca95-513">RADIX</span><span class="sxs-lookup"><span data-stu-id="1ca95-513">RADIX</span></span>|<span data-ttu-id="1ca95-514">Int16</span><span class="sxs-lookup"><span data-stu-id="1ca95-514">Int16</span></span>|
|<span data-ttu-id="1ca95-515">S POVOLENOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="1ca95-515">NULLABLE</span></span>|<span data-ttu-id="1ca95-516">Int16</span><span class="sxs-lookup"><span data-stu-id="1ca95-516">Int16</span></span>|
|<span data-ttu-id="1ca95-517">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="1ca95-517">REMARKS</span></span>|<span data-ttu-id="1ca95-518">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-518">String</span></span>|
|<span data-ttu-id="1ca95-519">PŘETÍŽENÍ</span><span class="sxs-lookup"><span data-stu-id="1ca95-519">OVERLOAD</span></span>|<span data-ttu-id="1ca95-520">Int32</span><span class="sxs-lookup"><span data-stu-id="1ca95-520">Int32</span></span>|
|<span data-ttu-id="1ca95-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="1ca95-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="1ca95-522">Int32</span><span class="sxs-lookup"><span data-stu-id="1ca95-522">Int32</span></span>|

### <a name="procedureparameters"></a><span data-ttu-id="1ca95-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="1ca95-523">ProcedureParameters</span></span>

|<span data-ttu-id="1ca95-524">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="1ca95-524">ColumnName</span></span>|<span data-ttu-id="1ca95-525">DataType</span><span class="sxs-lookup"><span data-stu-id="1ca95-525">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="1ca95-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="1ca95-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="1ca95-527">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-527">String</span></span>|
|<span data-ttu-id="1ca95-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="1ca95-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="1ca95-529">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-529">String</span></span>|
|<span data-ttu-id="1ca95-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="1ca95-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="1ca95-531">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-531">String</span></span>|
|<span data-ttu-id="1ca95-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="1ca95-532">COLUMN_NAME</span></span>|<span data-ttu-id="1ca95-533">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-533">String</span></span>|
|<span data-ttu-id="1ca95-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="1ca95-534">COLUMN_TYPE</span></span>|<span data-ttu-id="1ca95-535">Int16</span><span class="sxs-lookup"><span data-stu-id="1ca95-535">Int16</span></span>|
|<span data-ttu-id="1ca95-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="1ca95-536">DATA_TYPE</span></span>|<span data-ttu-id="1ca95-537">Int16</span><span class="sxs-lookup"><span data-stu-id="1ca95-537">Int16</span></span>|
|<span data-ttu-id="1ca95-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="1ca95-538">TYPE_NAME</span></span>|<span data-ttu-id="1ca95-539">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-539">String</span></span>|
|<span data-ttu-id="1ca95-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="1ca95-540">COLUMN_SIZE</span></span>|<span data-ttu-id="1ca95-541">Int32</span><span class="sxs-lookup"><span data-stu-id="1ca95-541">Int32</span></span>|
|<span data-ttu-id="1ca95-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="1ca95-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="1ca95-543">Int32</span><span class="sxs-lookup"><span data-stu-id="1ca95-543">Int32</span></span>|
|<span data-ttu-id="1ca95-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="1ca95-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="1ca95-545">Int16</span><span class="sxs-lookup"><span data-stu-id="1ca95-545">Int16</span></span>|
|<span data-ttu-id="1ca95-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="1ca95-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="1ca95-547">Int16</span><span class="sxs-lookup"><span data-stu-id="1ca95-547">Int16</span></span>|
|<span data-ttu-id="1ca95-548">S POVOLENOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="1ca95-548">NULLABLE</span></span>|<span data-ttu-id="1ca95-549">Int16</span><span class="sxs-lookup"><span data-stu-id="1ca95-549">Int16</span></span>|
|<span data-ttu-id="1ca95-550">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="1ca95-550">REMARKS</span></span>|<span data-ttu-id="1ca95-551">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-551">String</span></span>|
|<span data-ttu-id="1ca95-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="1ca95-552">COLUMN_DEF</span></span>|<span data-ttu-id="1ca95-553">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-553">String</span></span>|
|<span data-ttu-id="1ca95-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="1ca95-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="1ca95-555">Int16</span><span class="sxs-lookup"><span data-stu-id="1ca95-555">Int16</span></span>|
|<span data-ttu-id="1ca95-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="1ca95-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="1ca95-557">Int16</span><span class="sxs-lookup"><span data-stu-id="1ca95-557">Int16</span></span>|
|<span data-ttu-id="1ca95-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="1ca95-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="1ca95-559">Int32</span><span class="sxs-lookup"><span data-stu-id="1ca95-559">Int32</span></span>|
|<span data-ttu-id="1ca95-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="1ca95-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="1ca95-561">Int32</span><span class="sxs-lookup"><span data-stu-id="1ca95-561">Int32</span></span>|
|<span data-ttu-id="1ca95-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="1ca95-562">IS_NULLABLE</span></span>|<span data-ttu-id="1ca95-563">String</span><span class="sxs-lookup"><span data-stu-id="1ca95-563">String</span></span>|

## <a name="see-also"></a><span data-ttu-id="1ca95-564">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1ca95-564">See also</span></span>

- [<span data-ttu-id="1ca95-565">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="1ca95-565">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
